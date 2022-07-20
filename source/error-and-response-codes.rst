Error and response codes
************************
When debugging queries that aren't returning what you expect it can be useful to check the HTTP status code being returned by the API.
 
.. list-table:: 
   :widths: 20 80
   :header-rows: 1

   * - HTTP status code
     - Description
   * - ``200``
     - Success. The body of the response should contain the data you requested.  
   * - ``403``
     - You aren't authorized for this call. Some requests require an API key.
   * - ``404``
     - Altmetric doesn't have any details for the research output or set of research outputs you requested. 
   * - ``429``
     - You are being rate limited. If you haven't already then apply for an API key.
   * - ``502``
     - The API version you are using is currently down for maintenance.