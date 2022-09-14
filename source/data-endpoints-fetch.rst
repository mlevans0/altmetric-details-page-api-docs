Fetch
*****

Fetch detailed Altmetric information about a particular article or dataset. This call returns much more information about each mention than from the standard :ref:`Counts` Only endpoint and
allows users to see full details of the mentions, including the URLs to the mentions themselves. 

There are two exceptions with requests to this endpoint, Twitter and certain news sources that fall under UK licensing restrictions. You can read more about this on our :ref:`Limitations` page.

.. warning::
    Calls to this endpoint are only available to commercial license holders. If you call this endpoint without an authorized API key you'll get a ``403`` response. Contact us for pricing or to request use as a non-commercial entity.

This endpoint is optimized for specific queries about single research outputs. To use this endpoint you will need some programming knowledge but there are various *wrappers* in different
languages (see below) available on Github or you can choose to write your own software. 

Here are a few examples of third party wrappers that you can use to help you start consuming data from our API. Please note that they are built
and maintained by third party developers and are not supported directly by us.

- **R** : rAltmetric (https://cran.r-project.org/web/packages/rAltmetric/README.html) -- This package provides a way to programmatically retrieve altmetrics from various publication types (books, newsletters, articles, peer-reviewed papers and more) from altmetric.com. The package is really simple to use and only has two major functions: - altmetrics - Pass it a doi, isbn, uri, arxiv id or other to get metrics - altmetric_data Pass it the results from the previous call to get a tidy data.frame. 
- **Python** : PyAltmetric (https://github.com/CenterForOpenScience/PyAltmetric) -- PyAltmetric provides an easy python wrapper for the Altmetric API and provides methods to be Articles from API responses and preexisting JSON.
- **Ruby** : Altmetric (https://github.com/ldodds/altmetric) -- Provides a basic client object for interacting with the API. Provides quick access to the JSON results or direct access to API responses.

.. warning::
  These wrappers are built and maintained by third party developers and are not supported directly by us.

Request
=======

When making a request to the ``/fetch/`` API endpoint you will need to replace the placeholder ``key`` ``xxx-xxx-xxx-xxx``   in the examples below with your own API key, 
otherwise you'll receive the ``403 The API key you supplied was invalid.`` response from the server.
  
.. function:: GET /{version}/fetch/{identifier_type}/{id}?key=xxx-xxx-xxx-xxx

  Fetch a research output using the supplied identifier type and identifier

  **Example request**:

  .. code-block:: http

    GET /v1/fetch/doi/10.1038/news.2011.490?key=xxx-xxx-xxx-xxx HTTP/1.1
    Host: api.altmetric.com
  
  **Query parameters:**

  .. list-table:: 
    :widths: 20 20 30 30
    :header-rows: 1

    * - Parameter
      - Required
      - Accepts
      - Description
    * - ``version``
      - Yes
      - ``v1``
      - See :ref:`Versioning`
    * - ``identifier type``
      - Yes
      - ``doi`` ``handle`` ``pmid`` ``arxiv`` ``ads`` ``ssrn`` ``repec`` ``isbn`` ``id`` ``nct_id`` ``urn`` ``uri``
      - A valid identifier type 
    * - ``identifier``
      - Yes
      - A valid identifier of the type specified by ``identifier_type``
      - Identifiers should not be URL-encoded.
    * - ``include_sources``
      - 
      - Comma delimited list of ``post_types`` to include data for in the response.
      - Defaults to include everything.
    * - ``exclude_sources``
      - 
      - Comma delimited list of ``post_types`` to exclude data for in response.
      - Defaults to exclude nothing.
    * - ``include_sections``
      - 
      - Comma delimited list of response object sections to include. 

        Current supported sections are  ``counts`` ``citation`` ``altmetric_score`` ``demographics`` ``posts`` ``images``
      - Defaults to include everything.
    * - ``post_types``
      - 
      - Comma delimited list of additional filters on ``post_types``

        Current filters are: ``original_tweets``
      - Defaults to include everything. In this case retweets are excluded from response. Counts section is unaffected.
  
  .. include:: shared/status-codes.rst

.. warning::
    Altmetric Ids are transient and unstable over the medium term. For long term application it is recommended that persistent IDs such as DOIs, arXiv IDs or PMIDs are used instead.

Response object
===============
A ``GET`` request to the **Full Access** ``/fetch/`` endpoint returns a JSON object with the following keys.

.. csv-table::
   :file: shared/fetch-field-glossary.csv
   :widths: 30 10 60
   :header-rows: 1

The ``posts`` object has post types (blog post, tweet, Facebook wall post etc.) as keys and the posts of that type where a mention was found in arrays of post objects as the values.

For tweets you'll receive only tweet IDs and user profile IDs, not the content of the tweet itself or otherdetails about user profiles. You should use tweet IDs to fetch more
data from the `Twitter API <https://dev.twitter.com/docs>`_ using your own developer account or `embed tweets <https://dev.twitter.com/docs/embedded-tweets>`_ directly on your website.

Example response
================

.. literalinclude:: responses/fetch.json
  :language: JSON

Try it yourself
===============
Below is a list of example requests. Before using any of these examples within your application you will need to update the ``key`` to the one that you were issued. Alternatively you can enter your API key into the field below and click the **Authorize** button to launch the example request directly from the documentation.

.. raw:: html

    <script>
      function authorize() {
          let custom_api_key = document.getElementById('custom_api_key').value
          let paragraphs = Array.from(document.querySelectorAll('p'))
          paragraphs.filter(element => element.textContent.includes("xxx-xxx-xxx-xxx")).forEach(p => {
            let hrefs = Array.from(p.querySelectorAll('[href*="key=xxx-xxx-xxx-xxx"]'))
            hrefs.forEach(el => {
              let authorizedHref = el.href.replace("xxx-xxx-xxx-xxx", custom_api_key)
              el.href = authorizedHref
              el.innerHTML = authorizedHref
            })
        })
        const authorize_button = document.getElementById('authorize-btn');
        authorize_button.innerText = 'Authorized!';
        setTimeout(() => {
          authorize_button.innerText = 'Authorize';
        }, 1000);
      }
    </script>
  
  <div style="padding-bottom:30px">
      <label for="custom_api_key">Enter your API key here: </label>
      <input type="text" id="custom_api_key" value="xxx-xxx-xxx-xxx"></input>
      <button id="authorize-btn" class="guilabel" onclick="authorize()">Authorize</button>
  </div>

.. list-table:: 
   :widths: 50 50 
   :header-rows: 1

   * - Scenario
     - URL
   * - Fetch a research output by its Altmetric Id 
     - https://api.altmetric.com/v1/fetch/id/241939?key=xxx-xxx-xxx-xxx  
   * - Fetch a research output by its Digital Object Identifier
     - https://api.altmetric.com/v1/fetch/doi/10.1038/news.2011.490?key=xxx-xxx-xxx-xxx
   * - Fetch a research output by its PubMed Id
     - https://api.altmetric.com/v1/fetch/pmid/21148220?key=xxx-xxx-xxx-xxx 
   * - Fetch a research output by its arXiv Id
     - https://api.altmetric.com/v1/fetch/arxiv/1108.2455?key=xxx-xxx-xxx-xxx
   * - Fetch a research output by its bibcode Id
     - https://api.altmetric.com/v1/fetch/ads/2012apphl.100y3104b?key=xxx-xxx-xxx-xxx
   * - Fetch a research output by its ISBN number
     - https://api.altmetric.com/v1/fetch/isbn/978-3-319-25557-6?key=xxx-xxx-xxx-xxx