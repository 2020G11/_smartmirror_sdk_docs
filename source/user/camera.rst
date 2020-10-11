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

.. py:function:: getImage()

   Retrieve an Image-object from currently registered camera device. Serialize it before saving using user.config.

   :param: *None*
   :type: *None*
   :return: An image object captured.
   :rtype: Object

.. py:class:: GestureClient

   .. py:function:: listGestures()

      List the gestures available.

      :param: *None*
      :return: A list containing the default gestures which can be used to register trigger events. Default gestures
               include 'thumbsUp', 'thumbsDown', 'slideLeft' etc.
      :rtype: list
   
   .. py:function:: registerEvents(gesture, *events)

      Register the events to the specified gesture.

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

.. py:class:: ObjectClient

   .. py:function:: detectObjects()

        Capture objects from camera stream and return the corresponding Object objects (and their confidence values) if any object is detected. 
        The object can be serialized and saved using user.config or any other persistent storage mechanism. Support detection of multiple objects in a single frame as well.

        :param: *None*
        :type: *None*
        :return: A Python dict containing Object objects and confidence value as key-value pair. 
        :rtype: dict
