Counts
******
Fetches a research output by the provided supported unique identifier.

Supported identifiers
=====================

Altmetric id
------------

.. function:: GET /(version)/id/(id)

  Fetch research output using an internal Altmetric identifier

  **Example request**:

  .. code-block:: http

    GET /v1/id/241939 HTTP/1.1
    Host: api.altmetric.com
    
  :Query Parameters:

    - **version** : (*required*) -- see :ref:`Versioning`
    - **id** : (*required*) -- For example 241939
    - **key** : (*optional*) -- The API key that you were issued

  .. include:: shared/status-codes.rst

  Try it: https://api.altmetric.com/v1/id/241939 

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

  .. include:: shared/status-codes.rst

  Try it: https://api.altmetric.com/v1/doi/10.1038/news.2011.490

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

  .. include:: shared/status-codes.rst
  
  Try it: https://api.altmetric.com/v1/pmid/21148220

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

  .. include:: shared/status-codes.rst

  Try it: https://api.altmetric.com/v1/arxiv/1108.2455

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

  .. include:: shared/status-codes.rst

  Try it: https://api.altmetric.com/v1/ads/2012apphl.100y3104b

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

  .. include:: shared/status-codes.rst

  Try it: https://api.altmetric.com/v1/isbn/978-3-319-25557-6

Response object
===============
A GET request to the count only endpoint returns a JSON object.

.. csv-table::
   :file: tables/counts-and-citations-field-glossary.csv
   :widths: 30 10 60
   :header-rows: 1
 
Example response
================

.. literalinclude:: responses/counts.json
  :language: JSON