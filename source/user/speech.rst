.. _user.speech :

user.speech
============

This module is used to perform speech-to-text conversion. The attributes *encoding* and *sampleRate* will be auto-detected according to
the system's audio hardware. Attribute *languageCode* will be set to **en-US** by default.

.. py:class:: SpeechClient

   .. py:attribute:: (attr) encoding

      (required) specifies the encoding scheme of the supplied audio. Supported scheme includes
      MP3, FLAC, LINEAR16, MULAW, AMR, AMR_WB, OGG_OPUS, SPEEX_WITH_HEADER_BYTE.
   
   .. py:attribute:: (attr) sampleRate

      (required) specifies the sample rate (in Hertz) of the supplied audio.
   
   .. py:attribute:: (attr) languageCode

      (required) contains the language + region/locale to use for speech recognition of the supplied audio.

   .. py:function:: startClient(timeout=0)

      Performs bidirectional streaming speech recognition: receive results while receiving audio. Audio stream will be 
      retrieved from system's current active audio hardware when this function is called until timeout or terminated. It will
      reinitialize the speech client if called multiple times.

      :param float timeout: Timeout before the application stops receiving audio data in seconds. 0, set by default, for indefinite time.
      :return: *None*
      :rtype: *None*
   
   .. py:function:: stopClient()

      Terminate the receiving of audio stream for current SpeechClient instance.

      :param: *None*
      :return: *None*
      :rtype: *None*
   
   .. py:function:: getNaturalText()

      Return the converted text as a result of calling startClient() function. Can be called in between startClient() and stopClient()
      to receive intermediate, incomplete results.

      :param float timeout: *None*
      :return: A dict containing interim results and final results with their corresponding confidence values. Both interim and final 
               results are lists of zero or more possible results.
      :rtype: dict

      Sample Output:
      ::
         {
            "interim": {
               "this": 0.956, "api": 0.768, "is": 0.743, "amazing": 0.645, "nope": 0.889, "crocodile": 0.134
            },
            "final": {
               "this api is amazing nope": 0.988, "this eh p I is amazon nope": 0.532
            }
         }

Sample Code Snippet:
::
   import user.speech as speech

   speechClient = speech.AudioClient()

   # changing languageCode from default "en-US" to other languageCode
   speechClient.languageCode = "en-AU"

   # start receiving audio stream indefinitely
   speechClient.startClient(0)
   # after receiving input for some time...
   speechClient.stopClient()

   # get the key-value pair of the complete sentence with highest confidence value
   results = speechClient.getNaturalText().get("final")
   finalSentence = max(results.items(), key=lambda item:item[1])

   # example finalSentence would be: ("this api is amazing nope", 0.988)