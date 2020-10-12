.. _user.camera :

user.camera
============

This module is used to access camera related functionalities like gesture, faces and 
object recognition. Current system's camera device will be automatically detected and registered.

.. py:function:: onMotion(*events)

   Register the events for detected motion.

   :param events: A varying number of Event instances to be triggered when motion is detected.
   :type events: Event
   :return: *None*
   :rtype: *None*

Sample Code Snippet:
::
   import user.camera as camera

   # create an Event
   def switchOnLight():
      print("Boom! I am on.")

   event = camera.Event()
   event.setAction(switchOnLight)

   # set Event to be triggered when motion detected
   camera.onMotion(event)

.. py:function:: getImage()

   Retrieve an Image-object from currently registered camera device. Serialize it before saving using user.config.

   :param: *None*
   :type: *None*
   :return: An image object captured.
   :rtype: Object

Sample Code Snippet:
::
   import user.camera as camera
   import base64

   img = camera.getImage()
   # save the img after encoding with base64
   with open("img.png" , "wb") as fh:
      fh.write(base64.decodebytes(img))

   # load the image
   with open("img.png", "rb") as image_file:
      encoded_string = base64.b64encode(image_file.read())

.. py:class:: GestureClient

   .. py:function:: listGestures()

      List the gestures available.

      :param: *None*
      :return: A list containing the default gestures which can be used to register trigger events. Default gestures
               include 'thumbsUp', 'thumbsDown', 'slideLeft' etc.
      :rtype: list
   
   .. py:function:: registerEvents(gesture, *events)

      Register the events to the specified gesture.

      :param gesture: The gesture to trigger the event(s).
      :type gesture: Gesture
      :param events: A varying number of Event instances to be triggered when the specified gesture is detected.
      :type events: Event
      :return: *None*
      :rtype: *None*
   
   .. py:function:: startClient(timeout=0)

      Used to enable gesture recognition for current GestureClient instance.

      :param timeout: Timeout before the gesture recognition is disabled, in seconds.
      :type timeout: float
      :return: *None*
      :rtype: *None*

   .. py:function:: stopClient()

      Used to disable gesture recognition for current GestureClient instance.

      :param: *None*
      :type: *None*
      :return: *None*
      :rtype: *None*

Sample Code Snippet:
::
   import user.camera as camera

   # create an Event
   def switchOnLight():
      print("Boom! I am on.")
   
   def switchOnMusic():
      print("Boom! I am on too.")
   
   event1 = camera.Event()
   event.setAction(switchOnLight)

   event2 = camera.Event()
   event.setAction(switchOnMusic)

   # get the second gesture, 'thumbsUp' gesture in this example
   gestureClient = camera.GestureClient()
   thumbsUp = gestureClient.listGestures()[0]

   # user's 'thumbsUp' gesture will trigger both event1 and event2 in sequential order after gestureClient is started
   gestureClient.registerEvents(thumbsUp, event1, event2)

   gestureClient.startClient(0)
   # after some time...
   gestureClient.stopClient()

.. py:class:: Event

   .. py:function:: setAction(action)

      :param action: A python function used to define action.
      :type action: function
      :return: function
      :rtype: *None*

.. py:class:: FaceClient

    .. py:function:: detectFaces()

      Capture human faces from camera stream and return the corresponding Face objects if any face is detected. The object can be serialized and saved 
      using user.config or any other persistent storage mechanism. Support detection of multiple faces in a single frame.

      :param: *None*
      :type: *None*
      :return: The list of Face objects. 
      :rtype: list
   
    .. py:function:: faceSimilarity(faceOne, faceTwo)

      Compare and return the confidence value for similarity between two face objects.

      :param faceOne: The first face object.
      :type faceOne: Object
      :param faceTwo: The second face object to be compared with faceOne.
      :type faceTwo: Object
      :return: The confidence value for the similarity between the two Face objects.
      :rtype: float

Sample Code Snippet:
::
   import user.camera as camera
   import base64

   # get the user's face (standing in front of camera)
   faceClient = camera.FaceClient()
   userFace = faceClient.detectFaces()[0]

   # save the face after encoding with base64
   with open("face.png" , "wb") as fh:
      fh.write(base64.decodebytes(userFace))

.. py:class:: ObjectClient

   .. py:function:: detectObjects()

      Capture objects from camera stream and return the corresponding Object objects (and their confidence values) if any object is detected. 
      The object can be serialized and saved using user.config or any other persistent storage mechanism. Support detection of multiple objects in a single frame as well.

      :param: *None*
      :type: *None*
      :return: A Python dict containing Object objects and confidence value as key-value pair. 
      :rtype: dict
