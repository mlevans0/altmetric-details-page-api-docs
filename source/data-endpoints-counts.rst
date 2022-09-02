Counts
******
This endpoint provides information about individual research outputs. For example, you can query this endpoint using a DOI and retrieve the relevant Altmetric data. The API
is optimized for querying for a single identifier or a strictly defined search. 

Request
=======

.. function:: GET /(version)/(identifier_type)/(id)

  Fetch a research output using the supplied identifier type and identifier

  **Example request**:

  .. code-block:: http

    GET /v1/doi/10.1038/news.2011.490 HTTP/1.1
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
      - ``doi`` ``handle`` ``pmid`` ``arxiv`` ``ads`` ``ssrn`` ``repec`` ``isbn``
      - A valid identifier type.
    * - ``identifier``
      - Yes
      - A valid identifier of the type specified by ``identifier_type``
      - Identifiers should not be urlencoded.

  .. include:: shared/status-codes.rst

.. warning::
    Altmetric ids are transient and unstable over the medium term. For long term application it is recommended that persistent IDs such as DOI's, arXiv ID's or PMID's are used instead.

Response object
===============
A ``GET`` request to the **Counts Only** endpoint returns a JSON object with the following keys. 

.. csv-table::
   :file: shared/counts-and-citations-field-glossary.csv
   :widths: 30 10 60
   :header-rows: 1
 
Example response
================

.. literalinclude:: responses/counts.json
  :language: JSON

Try it yourself
===============
Click on any of the URLs below to view example responses for the listed scenarios. 

.. list-table:: 
   :widths: 50 50 
   :header-rows: 1

   * - Scenario
     - URL
   * - Fetch a research output by its Altmetric Id 
     - https://api.altmetric.com/v1/id/241939  
   * - Fetch a research output by its Digital Object Identifier
     - https://api.altmetric.com/v1/doi/10.1038/news.2011.490
   * - Fetch a research output by its PubMed Id
     - https://api.altmetric.com/v1/pmid/21148220 
   * - Fetch a research output by its arXiv Id
     - https://api.altmetric.com/v1/arxiv/1108.2455
   * - Fetch a research output by its bibcode Id
     - https://api.altmetric.com/v1/ads/2012apphl.100y3104b
   * - Fetch a research output by its ISBN number
     - https://api.altmetric.com/v1/isbn/978-3-319-25557-6