.. _user.graphic :

user.graphic
============

Graphic library resembles MVC pattern, a View function (`on_tick`) is called periodically (a render cycle).  To provide a user interface, a layout that contains all UIComponent has to be supplied via `render` function in each render cycle.

UIComponent is a base of a "renderable", common components are descendents of UIComponent, and can be created by calling their respective functions.

To see how graphic works, check out the demo widget (under Widget Overview).


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

.. py:function:: createCanvas(width, height, drawable=True, state=None)

   Create a canvas that can be drawn programmatically or manually by user.  
   The state of the canvas can be saved by calling `repr()`, and restored by passing it in in the argument.

   :param int width:
   :param int height:
   :param bool drawable:
   :param dict state:
   :rtype: UIComponent

.. py:function:: createSprite(url)

   Create a sprite component with alpha channel, this function is experimental

   :param str url: Path to the PNG file
   :return: A sprite component
   :rtype: UIComponent

.. py:function:: render(layout, width, height)

   Submit a layout to compositor for rendering.  Calling multiple times will overwrite the previous invocation.

   :param Layout layout: A main layout to be rendered
   :param int width:
   :param int height:

.. py:class:: UIComponent

.. py:class:: Layout

   Subclass of :py:class:`UIComponent`

   Enums: `LinearVertical`, `LinearHorizontal`

.. py:class:: LayoutType
