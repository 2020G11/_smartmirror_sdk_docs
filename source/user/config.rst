.. _user.config :

user.config
============
The *config* is a globally available instance which can be used to get/set key-value pairs.
This is a persistent storage.
::

   identity = config.get(Key, Value)

.. py:function:: listConfigs()

   Get a list of all available configs in key-value pair dict.

   :param: *None*
   :return: A dict of key-value pairs.
   :rtype: dict

.. py:function:: get(key)

   Get the value for the specified key.

   :param key: Key for the key-value pair.
   :type key: str
   :return: The corresponding value for the key in config.
   :rtype: Object

.. py:function:: set(key, value)

   Set the key-value pair in config.

   :param key: Key for the key-value pair.
   :type key: str
   :param value: Value for the key-value pair.
   :type value: Object
   :return: *None*
   :rtype: *None*

Sample Code Snippet:
::
   import user.config as config

   # setting value with widget name & attribute as key
   config.set("memo.itemCount", 3)

   # retrieve the value with corresponding key
   itemCount = config.get("memo.itemCount")

