Counts
******
Fetches a research output by the provided supported unique identifier.

Supported identifiers
=====================

Altmetric id
------------

.. function:: GET /(version)/id/(id))

  Fetch research output using an internal Altmetric identifier

  **Example request**:

  .. code-block:: http

        GET /v1/id/241939 HTTP/1.1
        Host: api.altmetric.com
    
  :Query Parameters:

      - **version** : (*required*) -- see :ref:`Versioning`
      - **id** : (*required*) -- For example 241939
      - **key** : (*optional*) -- The API key that you were issued

  :Status Codes:

      - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
      - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
      - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
      - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
      - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/id/241939 

.. warning::
    Altmetric IDs are transient and unstable over the medium term. For long term application it is recommended that persistent IDs such as DOI's, arXiv ID's or PMID's are used instead.

DOI
---

.. function:: GET /(version)/doi/(doi)

  Fetch research output using a Digital Object Identifier. 

  **Example request**:

  .. code-block:: http

      GET /v1/doi/10.1038/news.2011.490 HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

      - **version** : (*required*) -- see :ref:`Versioning`
      - **doi** : (*required*) -- For example 10.1038/news.2011.490. The DOI should not be urlencoded.
      - **key** : (*optional*) -- The API key that you were issued

  :Status Codes:

      - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
      - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
      - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
      - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
      - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/doi/10.1038/news.2011.490

PubMed
------

.. function:: GET /(version)/pmid/(pmid)

  Fetch research output using a unique identifier number used in PubMed. 

  **Example request**:

  .. code-block:: http

      GET /v1/pmid/21148220 HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **pmid** : (*required*) -- For example 21148220.
    - **key** : (*optional*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.
  
  Try it now: https://api.altmetric.com/v1/pmid/21148220

arXiv
-----

.. function:: GET /(version)/arxiv/(arxiv)

  Fetch research output using a unique identifier used in the open-access repository arXiv. 

  **Example request**:

  .. code-block:: http

      GET /v1/arxiv/1108.2455 HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **arxiv** : (*required*) -- For example 1108.2455.
    - **key** : (*optional*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/arxiv/1108.2455

ads
---

.. function:: GET /(version)/ads/(ads)

  Fetch research output using a 19 digit identifier which describes the journal article. 

  **Example request**:

  .. code-block:: http

      GET /v1/ads/2012apphl.100y3104b  HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **ads** : (*required*) -- For example 2012apphl.100y3104b.
    - **key** : (*optional*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/ads/2012apphl.100y3104b

ISBN
----

.. function:: GET /(version)/isbn/(isbn)

  Fetch research output using an ISBN. 

  **Example request**:

  .. code-block:: http

      GET /v1/isbn/978-3-319-25557-6 HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **isbn** : (*required*) -- For example 978-3-319-25557-6. The ISBN can be either ISBN-10 or ISBN-13 and does not need to be normalized.
    - **key** : (*optional*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/isbn/978-3-319-25557-6
 
Example response
================

.. literalinclude:: responses/counts.json
  :language: JSON
       
Field glossary
==============

Here's a list of all JSON fields available in the **Counts Only** version of the API.

.. csv-table::
   :file: tables/counts-field-glossary.csv
   :widths: 30 10 60
   :header-rows: 1

Fetch
*****

Fetch detailed altmetric information about a particular article or dataset. This call returns much more information about each mention than the standard counts query calls.

.. warning::
    This call is only available to commercial license holders. If you call it without an authorized API key you'll get a ``403`` response. Contact us for pricing or to request use as a non-commercial entity.


Supported identifiers
=====================
Below are a number of example calls that you can use to query the ``/fetch/`` API endpoint. Note that you will need to replace the key ``xxx-xxx-xxx-xxx`` with your own API key, otherwise you'll 
receive the ``403 The API key you supplied was invalid.`` response from the server.

.. raw:: html

    <label for="custom_api_key">Enter you API key here: </label>
    <input type="text" id="custom_api_key" value="xxx-xxx-xxx-xxx"></input>

    <script>
      function authorize() {
          let custom_api_key = document.getElementById('custom_api_key').value
          let paragraphs = Array.from(document.querySelectorAll('p'))
          paragraphs.filter(element => element.textContent.includes("Try it now:")).forEach(p => {
            let hrefs = Array.from(p.querySelectorAll('[href*="key=xxx-xxx-xxx-xxx"]'))
            hrefs.forEach(el => {
              let authorizedHref = el.href.replace("xxx-xxx-xxx-xxx", custom_api_key)
              el.href = authorizedHref
              el.innerHTML = authorizedHref
            })
        })
      }
    </script>

    <button class="guilabel" onclick="authorize()">Authorize</button>
    <br />
    <br />

Altmetric id
------------

.. function:: GET /(version)/fetch/id/(id)?key=xxx-xxx-xxx-xxx

  Fetch research output using an internal Altmetric identifier

  **Example request**:

  .. code-block:: http

      GET /v1/fetch/id/241939?key=xxx-xxx-xxx-xxx HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **id** : (*required*) -- For example 241939.
    - **key** : (*required*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/fetch/id/241939?key=xxx-xxx-xxx-xxx 

.. warning::
    Altmetric IDs are transient and unstable over the medium term. For long term application it is recommended that persistent IDs such as DOI's, arXiv ID's or PMID's are used instead.

DOI
---

.. function:: GET /(version)/fetch/doi/(doi)?key=xxx-xxx-xxx-xxx

  Fetch research output using a Digital Object Identifier. 

  **Example request**:

  .. code-block:: http

      GET /v1/fetch/doi/10.1038/news.2011.490?key=xxx-xxx-xxx-xxx HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **doi** : (*required*) -- For example 10.1038/news.2011.490. The DOI should not be urlencoded.
    - **key** : (*required*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/fetch/doi/10.1038/news.2011.490?key=xxx-xxx-xxx-xxx

PubMed
------

.. function:: GET /(version)/fetch/pmid/(pmid)?key=xxx-xxx-xxx-xxx

  Fetch research output using a unique identifier number used in PubMed. 

  **Example request**:

  .. code-block:: http
  
      GET /v1/fetch/pmid/21148220?key=xxx-xxx-xxx-xxx HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **pmid** : (*required*) -- For example 21148220.
    - **key** : (*required*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.
  
  Try it now: https://api.altmetric.com/v1/fetch/pmid/21148220?key=xxx-xxx-xxx-xxx

arXiv
-----

.. function:: GET /(version)/fetch/arxiv/(arxiv)?key=xxx-xxx-xxx-xxx

  Fetch research output using a unique identifier used in the open-access repository arXiv. 

  **Example request**:

  .. code-block:: http

      GET /v1/fetch/arxiv/1108.2455?key=xxx-xxx-xxx-xxx HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **arxiv** : (*required*) -- For example 1108.2455.
    - **key** : (*required*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/fetch/arxiv/1108.2455?key=xxx-xxx-xxx-xxx

ads
---

.. function:: GET /(version)/fetch/ads/(ads)?key=xxx-xxx-xxx-xxx

  Fetch research output using a 19 digit identifier which describes the journal article. 

  **Example request**:

  .. code-block:: http

      GET /v1/fetch/ads/2012apphl.100y3104b?key=xxx-xxx-xxx-xxx  HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **ads** : (*required*) -- For example 2012apphl.100y3104b.
    - **key** : (*required*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1/fetch/ads/2012apphl.100y3104b?key=xxx-xxx-xxx-xxx

ISBN
----

.. function:: GET /(version)/fetch/isbn/(isbn)?key=xxx-xxx-xxx-xxx

  Fetch research output using an ISBN. 

  **Example request**:

  .. code-block:: http

      GET /v1/fetch/isbn/978-3-319-25557-6?key=xxx-xxx-xxx-xxx HTTP/1.1
      Host: api.altmetric.com
  
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **isbn** : (*required*) -- For example 978-3-319-25557-6. The ISBN can be either ISBN-10 or ISBN-13 and does not need to be normalized.
    - **key** : (*required*) -- The API key that you were issued

  :Status Codes:

    - `200 OK <https://www.rfc-editor.org/rfc/rfc9110.html#name-200-ok>`_ -- The body of the response should contain the data you requested.
    - `403 Forbidden <https://www.rfc-editor.org/rfc/rfc9110.html#name-403-forbidden>`_ -- You aren't authorized for this call. Some requests require an API key.
    - `404 Not Found <https://www.rfc-editor.org/rfc/rfc9110.html#name-404-not-found>`_ -- Altmetric doesn't have any details for the research output or set of research outputs you requested. 
    - `429 Too Many Requests <https://www.rfc-editor.org/rfc/rfc6585#section-4>`_ -- You are being rate limited. If you haven't already then apply for an API key.
    - `502 Bad Gateway <https://www.rfc-editor.org/rfc/rfc9110.html#name-502-bad-gateway>`_ -- The API version you are using is currently down for maintenance.

  Try it now: https://api.altmetric.com/v1//fetch/isbn/978-3-319-25557-6?key=xxx-xxx-xxx-xxx

Parameters
==========

.. list-table:: 
   :widths: 20 20 30 30
   :header-rows: 1

   * - Parameter
     - Required
     - Accepts
     - Description
   * - ``identifier type``
     - Yes
     - A valid identifier type  
     - Types currently accepted are: ``doi`` ``handle`` ``pmid`` ``arxiv_id`` ``ads_id`` ``ssrn`` ``repec id`` 
   * - ``identifier``
     - Yes
     - A valid identifier of the type specified by identifier type
     - e.g. the actual DOI PubMed ID etc.
   * - ``include_sources``
     - No
     - Comma delimited list of ``post_types`` to include data for in the response.
     - Defaults to including everything.
   * - ``exclude_sources``
     - No
     - Comma delimited list of ``post_types`` to exclude data for in response
     - Defaults to exclude nothing.
   * - ``include_sections``
     - No
     - Comma delimited list of response object sections to include
     - Defaults to including everything. Current sections are: ``counts`` ``citation`` ``altmetric_score`` ``demographics`` ``posts`` ``images``
   * - ``post_types``
     - No
     - Comma delimited list of additional filters on post types.
     - Defaults to including everything. Current filters are: ``original_tweets`` In this case retweets are excluded from response. Counts section is unaffected.

Response object
===============
A ``GET`` request to the ``/fetch/`` endpoint returns a JSON object.

.. list-table:: 
   :widths: 20 80
   :header-rows: 1

   * - Parameter
     - Descritpion
   * - ``counts``
     - Provides the number of mentions and unique authors in each relevant source type, for example ``blogs`` ``twitter`` ``news`` as well as reference manager reader counts and downloads, where available.
   * - ``citation``
     - Bibliographic metadata about the output requested. You'll find third party identifiers, for example ``doi`` ``pmid`` ``arxiv`` etc here.
   * - ``altmetric_score``
     - Contains details of the Altmetric score and, where possible, provides some context.
   * - ``demographics``
     - Altmetric categorizes users from some sources based on their posting history and profile information. Counts for each category are included in this section along with geolocation data.
   * - ``posts``
     - The ``posts`` object has post types (blog post, tweet, Facebook wall post etc.) as keys and the posts ofthat type where a mention was found in arrays of post objects as the values.

       Titles, snippets and authorinformation are included for each mention when available. Use the ``include_sources`` or ``exclude_sources`` parameter if you only want details from certain sources. 

       For tweets you'll receive only tweet IDs and user profile IDs, not the content of the tweet itself or otherdetails about user profiles. You should use tweet IDs to fetch more data from the Twitter API using your own  developer account or embed tweets directly on your website. 

       A maximum of 1--500--000 tweet IDs can beretrieved in any rolling 30 day period. Thereafter you'll get an error message: to continue using this calluse the ``exclude_sources`` parameter to exclude tweets from your results. If you are interested in original tweets only you can use the ``post_types`` parameter to exclude retweets fromyour results and delay reaching the maximum tweet IDs limit.

       Note that when fetching and displaying tweets you should be adhering to Twitter's `display guidelines <https://dev.twitter.com/terms/display-guidelines>`_ and `developer policy <https://developer.twitter.com/en/developer-terms/policy.html>`_.

Example response
================

.. literalinclude:: responses/fetch.json
  :language: JSON

Citations
*********
List research outputs with activity in a given timeframe (see the ``timeframe`` parameter in the table below for supported values).

Parameters
==========

.. list-table:: 
   :widths: 20 10 35 35
   :header-rows: 1 

   * - Paramter
     - Required
     - Accepts
     - Description
   * - ``timeframe``
     - Yes 
     - ``at`` ``1d`` ``2d`` ``3d`` ``4d`` ``5d`` ``6d`` ``1w`` ``1m`` ``3m`` ``1y``
     - Include only research outputs which have seen activity in the past x days / weeks / months. 
       
       Use ``at`` for "all time": all of the research outputs in the Altmetric database.
   * - ``page``
     -  
     - integer
     - Page number used to paginate through results. First page is page ``1``. 

       The API will return an error if you ask for a page number beyond (number of research outputs / ``num_results``)
   * - ``num_results``
     -  
     - integer > ``0`` and < ``100``
     - Number of research outputs per page. Defaults to 25.
   * - ``cited_in``
     -  
     - One or more comma delimited options from: ``facebook`` ``blogs`` ``linkedin`` ``video`` ``rh`` ``gplus`` ``twitter`` ``reddit`` ``news`` ``f1000`` ``qna`` ``forum`` ``peerreview`` ``pinterest``
     - Include only research outputs mentioned in the supplied list of sources.
   * - ``doi_prefix``
     -  
     - A DOI prefix (for example 10.1038)
     - Include only research outputs with a DOI that contains the given prefix.
   * - ``order_by``
     -  
     - One of the following: ``score`` ``at_score`` ``readers`` ``first_seen`` ``pubdate``
     - Specifies the order in which the returned research outputs are listed. 
       
       If omitted, a value of ``score`` will be assumed. For explanations of each value, see :ref:`Sorting`.

Pagination
==========
Results from this endpoint are paginated. To help with paging through the list of results a ``query`` object is embeded in each response. 

.. list-table:: 
   :widths: 20 80
   :header-rows: 1

   * - Key
     - Description
   * - ``total``
     - The total number of research outputs that match the query parameters  
   * - ``page``
     - The current page that you are on
   * - ``num_results``
     - The number of research outputs in the current page 

Example
-------
Here we can see that we are currently on page 1 and we have been returned 25 results of a possible 100.

.. code-block:: json

    {
        "query": {
            "total": 100,
            "page": 1,
            "num_results": 25
        },
        "results" : [ ]
    } 

To get the next page you'd need to make the following request:

``curl https://api.altmetric.com/v1/citations/at?page=2``

To page through the entire list of research outputs: while ``query.page`` multiplied by ``query.num_results`` is less-than ``query.total`` you will need to keep incrementing the ``page``
query string integer value. In the example here we'd just need to increment ``page`` up to 4 (4 x 25 = 100).

Sorting
=======
Use of the ``order_by`` parameter will determine the order in which research outputs are listed within the response of the request.

.. list-table:: 
   :widths: 20 80
   :header-rows: 1

   * - Parameter
     - Description
   * - ``score (default)``
     - Orders research outputs based on the Altmetric attention score gained during the period defined by the timeframe argument supplied
   * - ``at_score``
     - Orders research outputs based on their overall Altmetric attention score
   * - ``readers``
     - Orders research outputs based on the number of Mendeley readers 
   * - ``first_seen``
     - Orders research outputs based on when Altmetric first started tracking mentions
   * - ``pubdate``
     - Orders research outputs based on their publication date

Response object
===============
The Altmetric Details Page API returns JSON. The ``/citations/`` endpoint returns an object with with the keys ``query`` and ``results``.

Query
-----

.. list-table:: 
   :widths: 20 20 60
   :header-rows: 1

   * - Parameter
     - Required
     - Notes
   * - ``query``
     - Yes
     - Metadata about your query.
   * - ``results``
     - Yes
     - Array of citation objects detailed below. May be empty if ``query.count`` is 0.

Example response
================

.. literalinclude:: responses/citations.json
  :language: JSON


Try it yourself
===============
Click on any of the URLs below to view example responses for the listed scenarios. 

API response samples
--------------------

.. list-table:: 
   :widths: 50 50 
   :header-rows: 1

   * - Scenario
     - URL
   * - To return the first 25 research outputs that have been mentioned in the past day
     - https://api.altmetric.com/v1/citations/1d  
   * - And then get the next 25
     - https://api.altmetric.com/v1/citations/1d?page=2
   * - Get 100 research outputs mentioned in the past week ordered by the altmetric attention score for that week
     - https://api.altmetric.com/v1/citations/1w?num_results=100 
   * - Get 100 research outputs mentioned on Reddit in the past week
     - https://api.altmetric.com/v1/citations/1w?num_results=100&cited_in=reddit
   * - Get 25 research outputs mentioned on Twitter in the past week ordered by the all time altmetric attention score
     - https://api.altmetric.com/v1/citations/1w?&cited_in=twitter&order_by=at_score
   * - Get the top 10 research outputs where the score has changed in the last month for the journal **History**
     - https://api.altmetric.com/v1/citations/1m?num_results=10&issns=00182648&order_by=score

Code samples
------------
Below are some snippets of code that help visualise how you can use the data returned from the ``/citations/`` endpoint.

Top 10 by score for journal
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Get the 10 most recently scored research outputs where the score has changed within the last month for the journal **History**

.. code-block:: javascript

     function renderTopTen() {
        fetch("https://api.altmetric.com/v1/citations/1m?num_results=10&issns=00182648&order_by=score")
        .then((data) => {
          return data.json()
        }).then((data) => {
          let top10 = document.getElementById('top10'), div = document.createElement('div');
          if (data.hasOwnProperty('results')) {
            top10.innerHTML = '';
            data.results.map(result => {
              div.innerHTML = `<li><a href="${result.details_url}"><img src="${result.images.small}" width=32 height=32 alt>${result.title}</a></li>`;
              top10.appendChild(div.firstChild);
            })
          }
      });    
    }

.. raw:: html

    <ol id="top10"></ol>
    <label for="issns">Customize this snippet by entering a single ISSN or a comma separated list</label>
    <input type="text" id="issns" value="00182648"></input>

    <script>
      function validateIssns(issns) {
        return issns.split(",").every(issn => Number.isInteger(+issn))
      }

      function renderTopTen() {
        let issns = document.getElementById('issns').value

        if(!validateIssns(issns)) {
          return alert("Please enter a single ISSN number or a comma separated list")
        }

        fetch(`https://api.altmetric.com/v1/citations/1m?num_results=10&issns=${issns}&order_by=score`)
        .then((data) => {
          return data.json()
        }).then((data) => {
          let top10 = document.getElementById('top10'), div = document.createElement('div');
          if (data.hasOwnProperty('results')) {
            top10.innerHTML = '';
            data.results.map(result => {
              div.innerHTML = `<li><a href="${result.details_url}"><img src="${result.images.small}" width=32 height=32 alt>${result.title}</a></li>`;
              top10.appendChild(div.firstChild);
            })
          }
        });    
      }
    </script>

    <button class="guilabel" onclick="renderTopTen()">Try it</button>

    <br />
    <br />   