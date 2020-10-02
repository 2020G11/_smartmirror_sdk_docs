.. _user.gesture :

user.gesture
============

This module is used to perform gesture recognition, registration and setting triggers.

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
   
   .. py:function:: enableGesture(timeout)

      Used to enable gesture recognition for current GestureClient instance.

      :param timeout: Timeout before the gesture recognition is disabled, in seconds.
      :type timeout: float
      :return: *None*
      :rtype: *None*

   .. py:function:: disableGesture()

      Used to disable gesture recognition for current GestureClient instance.

.. py:class:: Event

   .. py:function:: setAction(action)

      :param action: A python function used to define action.
      :return: function
      :rtype: *None*
