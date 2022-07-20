Access
******

Authentication
==============
The Details page API uses an API key for authorization. This key is a token that allows our application to verify that you are authorized to use the API and should be included when making requests. To do this you will need to include a
query string parameter named ``key`` that contains your assigned API key.

For example, if your key was ``xxx-xxx-xxx-xxx`` your request would look like this: ``curl 'http://api.altmetric.com/v1/id/241939?key=xxx-xxx-xxx-xxx'``

If you are a scientometrics researcher, you don't need to register for an API key to use the rate-limited **Details Page API - Counts Only**, but it is highly recommended that you do. 

If you wish to use the **Details Page API - Counts Only** without rate limiting, you must obtain an API key. Please `visit our website for more information <https://www.altmetric.com/research-access/>`_.

If you would like to use the **Details Page API** for commercial purposes, you will need to obtain an API key. Please email info@altmetric.com for more information.

Versioning
==========
To ensure that the code you develop remains functional for as long as possible - endpoints will be assigned new revision numbers if breaking changes are introduced. The current Details Page API version is ``v1`` and should be the version that you should use in production.

You can specify which version of the API to use by changing the base URL for your requests, for example to use ``v1`` you should use ``https://api.altmetric.com/v1/`` and your actual request should look like:

``https://api.altmetric.com/v1/citations/1d``

``https://api.altmetric.com/v1/doi/10.1038/480426a``

Limitations
***********
Cross-site scripting
====================
To support older browsers you can use JSONP. To do this you will need to include a ``callback`` parameter that contains the name of the Javascript function to invoke when the call returns.

For example: ``https://api.altmetric.com/v1/doi/10.1038/480426a?callback=my_callback``

You can try this now: https://api.altmetric.com/v1/doi/10.1038/480426a?callback=my_callback

.. warning:: 
    Altmetric is quite strict about what constitutes as a valid callback - only letters, digits and underscores are allowed.

Rate limiting
=============
Every day the Details Page API handles many thousands of requests. To help manage the volume of these requests, limits are placed on the number of requests that can be made from a
specific IP address and API key. These limits help us provide a reliable and dependable API service that serves the altmetric communitiy. 

You can check the ``X-HourlyRateLimit-Limit`` and ``X-DailyRateLimit-Limit`` headers for the current limits. The ``X-HourlyRateLimit-Remaining`` and ``X-DailyRateLimit-Remaining`` headers will tell you how many calls you have remaining.

When your rate limit has been exceeded, a ``429 'Too many requests'`` error is returned by the API.  When this occurs it is recommended that you examine HTTP headers above and pause requests until sufficient time has past. If you find that
you frequently hit the rate limit then you might want to consider throttling your requests or purchasing a commerical API key.