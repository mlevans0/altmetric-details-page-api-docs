Fetch
*****

Fetch detailed altmetric information about a particular article or dataset. This call returns much more information about each mention than the standard :ref:`Counts` Only query.

.. warning::
    Calls to this endpoint are only available to commercial license holders. If you call this endpoint without an authorized API key you'll get a ``403`` response. Contact us for pricing or to request use as a non-commercial entity.

Supported identifiers
=====================

.. note::
  When making a request to the ``/fetch/`` API endpoint you will need to replace the placeholder key ``xxx-xxx-xxx-xxx``   in the examples below with your own API key, 
  otherwise you'll receive the ``403 The API key you supplied was invalid.`` response from the server. 
  
  Alternatively, you can enter your API key into the field below and click the **Authorize** button to launch the example request directly from the documentation.

.. raw:: html

    <label for="custom_api_key">Enter your API key here: </label>
    <input type="text" id="custom_api_key" value="xxx-xxx-xxx-xxx"></input>
    <span id="custom_api_key"></span>

    <script>
      function authorize() {
          let custom_api_key = document.getElementById('custom_api_key').value
          let paragraphs = Array.from(document.querySelectorAll('p'))
          paragraphs.filter(element => element.textContent.includes("Try it:")).forEach(p => {
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

  Fetch a research output using an internal Altmetric identifier

  **Example request**:

  .. code-block:: http

    GET /v1/fetch/id/241939?key=xxx-xxx-xxx-xxx HTTP/1.1
    Host: api.altmetric.com
  
  **Query parameters:**

  .. list-table::
    :widths: 20 10 35 35
    :header-rows: 1 

    * - Parameter
      - Required
      - Accepts
      - Description
    * - ``version``
      - Yes
      - ``v1``
      - See :ref:`Versioning`      
    * - ``id``
      - Yes
      - An altmetric article id
      - For example 241939
    * - ``key``
      - Yes
      -  
      - The API key that you were issued
  
  .. include:: shared/status-codes.rst

  **Try it:** https://api.altmetric.com/v1/fetch/id/241939?key=xxx-xxx-xxx-xxx 

.. warning::
    Altmetric ids are transient and unstable over the medium term. For long term application it is recommended that persistent IDs such as DOI's, arXiv ID's or PMID's are used instead.

DOI
---

.. function:: GET /(version)/fetch/doi/(doi)?key=xxx-xxx-xxx-xxx

  Fetch a research output using a Digital Object Identifier. 

  **Example request**:

  .. code-block:: http

    GET /v1/fetch/doi/10.1038/news.2011.490?key=xxx-xxx-xxx-xxx HTTP/1.1
    Host: api.altmetric.com
  
 **Query parameters:**

  .. list-table::
    :widths: 20 10 35 35
    :header-rows: 1 

    * - Parameter
      - Required
      - Accepts
      - Description
    * - ``version``
      - Yes
      - ``v1``
      - See :ref:`Versioning`      
    * - ``doi``
      - Yes
      - Any valid DOI
      - For example 10.1038/news.2011.490. The DOI should not be urlencoded.
    * - ``key``
      - Yes
      -  
      - The API key that you were issued

  .. include:: shared/status-codes.rst

  **Try it:** https://api.altmetric.com/v1/fetch/doi/10.1038/news.2011.490?key=xxx-xxx-xxx-xxx

PubMed
------

.. function:: GET /(version)/fetch/pmid/(pmid)?key=xxx-xxx-xxx-xxx

  Fetch a research output using a unique identifier number used in PubMed. 

  **Example request**:

  .. code-block:: http
  
    GET /v1/fetch/pmid/21148220?key=xxx-xxx-xxx-xxx HTTP/1.1
    Host: api.altmetric.com
  
  **Query parameters:**

  .. list-table::
    :widths: 20 10 35 35
    :header-rows: 1 

    * - Parameter
      - Required
      - Accepts
      - Description
    * - ``version``
      - Yes
      - ``v1``
      - See :ref:`Versioning`      
    * - ``pmid``
      - Yes
      - Any valid PMID
      - For example 21148220
    * - ``key``
      - Yes
      -  
      - The API key that you were issued

  .. include:: shared/status-codes.rst
  
  **Try it:** https://api.altmetric.com/v1/fetch/pmid/21148220?key=xxx-xxx-xxx-xxx

arXiv
-----

.. function:: GET /(version)/fetch/arxiv/(arxiv)?key=xxx-xxx-xxx-xxx

  Fetch a research output using a unique identifier used in the open-access repository arXiv. 

  **Example request**:

  .. code-block:: http

    GET /v1/fetch/arxiv/1108.2455?key=xxx-xxx-xxx-xxx HTTP/1.1
    Host: api.altmetric.com
  
   **Query parameters:**

  .. list-table::
    :widths: 20 10 35 35
    :header-rows: 1 

    * - Parameter
      - Required
      - Accepts
      - Description
    * - ``version``
      - Yes
      - ``v1``
      - See :ref:`Versioning`      
    * - ``arxiv``
      - Yes
      - Any valid arXiv id
      - For example 1108.2455
    * - ``key``
      - Yes
      -  
      - The API key that you were issued

  .. include:: shared/status-codes.rst

  **Try it:** https://api.altmetric.com/v1/fetch/arxiv/1108.2455?key=xxx-xxx-xxx-xxx

ads
---

.. function:: GET /(version)/fetch/ads/(ads)?key=xxx-xxx-xxx-xxx

  Fetch a research output using a 19 digit identifier which describes the journal article. 

  **Example request**:

  .. code-block:: http

    GET /v1/fetch/ads/2012apphl.100y3104b?key=xxx-xxx-xxx-xxx  HTTP/1.1
    Host: api.altmetric.com
  
   **Query parameters:**

  .. list-table::
    :widths: 20 10 35 35
    :header-rows: 1 

    * - Parameter
      - Required
      - Accepts
      - Description
    * - ``version``
      - Yes
      - ``v1``
      - See :ref:`Versioning`      
    * - ``ads``
      - Yes
      - Any valid ADS bibcode
      - For example 2012apphl.100y3104b.
    * - ``key``
      - Yes
      -  
      - The API key that you were issued

  .. include:: shared/status-codes.rst

  **Try it:** https://api.altmetric.com/v1/fetch/ads/2012apphl.100y3104b?key=xxx-xxx-xxx-xxx

ISBN
----

.. function:: GET /(version)/fetch/isbn/(isbn)?key=xxx-xxx-xxx-xxx

  Fetch a research output using an ISBN. 

  **Example request**:

  .. code-block:: http

    GET /v1/fetch/isbn/978-3-319-25557-6?key=xxx-xxx-xxx-xxx HTTP/1.1
    Host: api.altmetric.com
  
   **Query parameters:**

  .. list-table::
    :widths: 20 10 35 35
    :header-rows: 1 

    * - Parameter
      - Required
      - Accepts
      - Description
    * - ``version``
      - Yes
      - ``v1``
      - See :ref:`Versioning`      
    * - ``isbn``
      - Yes
      - Any valid ISBN
      - For example 978-3-319-25557-6. The ISBN can be either ISBN-10 or ISBN-13 and does not need to be normalized.
    * - ``key``
      - Yes
      -  
      - The API key that you were issued

  .. include:: shared/status-codes.rst

  **Try it:** https://api.altmetric.com/v1//fetch/isbn/978-3-319-25557-6?key=xxx-xxx-xxx-xxx

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

       For tweets you'll receive only tweet IDs and user profile IDs, not the content of the tweet itself or otherdetails about user profiles. You should use tweet IDs to fetch more data from the `Twitter API <https://dev.twitter.com/docs>`_ using your own  developer account or `embed tweets <https://dev.twitter.com/docs/embedded-tweets>`_ directly on your website. 

       A maximum of 1--500--000 tweet IDs can beretrieved in any rolling 30 day period. Thereafter you'll get an error message: to continue using this calluse the ``exclude_sources`` parameter to exclude tweets from your results. If you are interested in original tweets only you can use the ``post_types`` parameter to exclude retweets fromyour results and delay reaching the maximum tweet IDs limit.

       Note that when fetching and displaying tweets you should be adhering to Twitter's `display guidelines <https://dev.twitter.com/terms/display-guidelines>`_ and `developer policy <https://developer.twitter.com/en/developer-terms/policy.html>`_.

Example response
================

.. literalinclude:: responses/fetch.json
  :language: JSON

Field glossary
==============

Here's a list of all JSON fields available in the **Full access** version of the API.