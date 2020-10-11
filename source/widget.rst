.. _widget :

Widget Overview
===============

A Widget is an application that the smart mirror user will be interacting with.  It takes up a part of the 'mirror' (i.e. display), and have access to collections of simple to use API.  To create a Widget, a structure has to be followed.

A Widget is defined primarily with its visual state representation.  It should define an on_tick function, which will be called periodically, and is expected to return a Layout, containing its UIComponent.


1. main.py - This is the main source file of your Widget, it should contain necessary functions

2. on_tick() - This is the most vital function that must be defined in main.py.

3. WIDGETSPEC.yml - This file contains the metadata of your Widget, primarily used by the package manager (for the user to search and (un)install Widget easily)

A demo widget is available here: https://github.com/2020G11/demo_saynote

A demo app repo showcasing how WIDGETSPEC.yml and git repo can be used for user application store is available here: https://github.com/2020G11/demo_app_repo
