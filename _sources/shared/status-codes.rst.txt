**HTTP status codes:**

.. list-table:: 
   :widths: 30 70
   :header-rows: 1 

   * - Code
     - Description
   * - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_
     - The body of the response should contain the data you requested. 
   * - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_
     - You aren't authorized for this call. Some requests require an API key.
   * - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_
     - Altmetric doesn't have any details for the research output or set of research outputs you requested.
   * - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_
     - You are being rate limited. If you haven't already then apply for an API key.
   * - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_
     -  The API version you are using is currently down for maintenance.