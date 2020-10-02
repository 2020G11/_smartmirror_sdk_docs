.. _user.graphic :

user.graphic
============

.. py:function:: createLayout(type)

   Create a layout of a given type

   :param LayoutType type:
   :return: A layout
   :rtype: Layout

.. py:function:: addComponentToLayout(layout, component)

   Add a component to a layout.  Layout can be nested

   :param Layout layout:
   :param UIComponent component:

.. py:function:: createText(text)

   Create a text component

   :param str text:
   :return: A text component
   :rtype: UIComponent

.. py:function:: createButton(buttonText, functionName)

   Create a button component, with an event handler

   :param str buttonText:
   :param str functionName:
   :return: A button component
   :rtype: UIComponent

.. py:function:: createSprite(url)

   Create a sprite component with alpha channel, this function is experimental

   :param str url: Path to the PNG file
   :return: A sprite component
   :rtype: UIComponent

.. py:function:: render(layout)

   Submit a layout to compositor for rendering.  Calling multiple times will overwrite the previous invocation

   :param Layout layout: A main layout to be rendered

.. py:class:: UIComponent

.. py:class:: Layout

   Subclass of :py:class:`UIComponent`

.. py:class:: LayoutType
