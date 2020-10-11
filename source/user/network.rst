.. _user.network :

user.network
============
The *network* module is used mainly for fetching data from publicly available API like Yahoo Finance API.

.. py:function:: fetch(URL, [options])

   A general purpose function for sending network requests. Works just like `fetch API <https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API>`_.
   Without options, that is a simple GET request, downloading the contents of the url. This is a blocking function.

   :param URL: The URL for the network request.
   :type URL: str
   :param options: A dict containing the optional parameters: method, headers etc.
   :type options: dict
   :return: A Response object containing the request status and data.
   :rtype: Response

Example:
::

   # read the response and return as text
   textResp = response.text() 
   # parse the response as JSON
   jsonResp = response.json() 
   
.. py:class:: Response
