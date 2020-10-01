.. _user.speech :

user.speech
============

This module is used to perform speech-to-text conversion.

.. py:class:: AudioClient

   .. py:attribute:: (attr) encoding

      (required) specifies the encoding scheme of the supplied audio. Supported scheme includes
      MP3, FLAC, LINEAR16, MULAW, AMR, AMR_WB, OGG_OPUS,SPEEX_WITH_HEADER_BYTE
   
   .. py:attribute:: (attr) sampleRate

      (required) specifies the sample rate (in Hertz) of the supplied audio.
   
   .. py:attribute:: (attr) languageCode

      (required) contains the language + region/locale to use for speech recognition of the supplied audio.

   .. py:function:: recognize(timeout)

      Performs bidirectional streaming speech recognition: receive results while receiving audio. Audio stream will be 
      retrieved from system's current active audio hardware when this function is called until timeout or terminated.

      :param float timeout: Timeout before the application stops receiving audio data in seconds.
      :return: A dict containing interim results and final results with their corresponding confidence values. Both interim and final 
               results are lists of zero or more possible results.
      :rtype: dict
   
   .. py:function:: terminate()

      Terminate the receiving of audio stream for current AudioClient instance.

      :param: *None*
      :return: *None*
      :rtype: *None*
