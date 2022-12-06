Citations
*********

Returns a list of research outputs with activity in the provided ``timeframe``.

Request
=======

.. function:: GET /{version}/citations/{timeframe}

  Returns a list of research outputs with activity in the provided time frame.

  **Example request**:

  .. code-block:: http

    GET /v1/citations/1m HTTP/1.1
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
    * - ``timeframe``
      - Yes 
      - ``at`` ``1d`` ``2d`` ``3d`` ``4d`` ``5d`` ``6d`` ``1w`` ``1m`` ``3m`` ``1y``
      - Include only research outputs which have seen activity in the past x days / weeks / months. 
        
        Use ``at`` for "all time": all of the research outputs in the Altmetric database.
    * - ``page``
      -  
      - integer
      - Page number used to paginate through results. First page is page ``1``. 

        The API will return an error if you ask for a page number beyond (number of research outputs / ``num_results``).
    * - ``num_results``
      -  
      - integer > ``0`` and < ``100``
      - Number of research outputs per page. Defaults to 25.
    * - ``cited_in``
      -  
      - One or more comma delimited options from: ``facebook`` ``blogs`` ``linkedin`` ``video`` ``pinterest`` ``gplus`` ``twitter`` ``reddit`` ``news`` ``f1000`` ``rh`` ``qna`` ``forum`` ``peerreview`` ``policy`` ``weibo`` 
      - Include only research outputs mentioned in the supplied list of sources.
    * - ``doi_prefix``
      -  
      - A DOI prefix (for example 10.1038)
      - Include only research outputs with a DOI that contains the given prefix.
    * - ``issn``
      -  
      - Accepts a comma separated list of ISSN's. Both ``00221465`` and ``0022-1465`` are accepted values.
      - A valid journal ISSN number. Must be a journal already registered and accessible from within the Altmetric Explorer.
    * - ``order_by``
      -  
      - One of the following: ``score`` ``at_score`` ``readers`` ``first_seen`` ``pubdate``
      - Specifies the order in which the returned research outputs are listed. 
        
        If omitted, a value of ``score`` will be assumed. For explanations of each value, see :ref:`Sorting`.
    * - ``key``
      -  
      - 
      - The API key that you were issued. 

  .. include:: shared/status-codes.rst

  **Try it:** https://api.altmetric.com/v1/citations/1m

Pagination
==========
Results from this endpoint are paginated. To help with paging through the list of results a ``query`` object is embedded in each response. 

.. list-table:: 
   :widths: 20 80
   :header-rows: 1

   * - Key
     - Description
   * - ``total``
     - The total number of research outputs that match the query parameters.  
   * - ``page``
     - The current page that you are on.
   * - ``num_results``
     - The number of research outputs in the current page. 

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
query string integer value. In the example here we'd just need to increment the ``page`` up to 4 (4 x 25 = 100).

Sorting
=======
Use of the ``order_by`` parameter will determine the order in which research outputs are listed within the response of the request.

.. list-table:: 
   :widths: 20 80
   :header-rows: 1

   * - Parameter
     - Description
   * - ``score (default)``
     - Orders research outputs based on the Altmetric attention score gained during the period defined by the timeframe argument supplied. For example, if the timeframe is ``1d``, the
       article which gained the most attention in the last 24 hours will be at the top.
   * - ``at_score``
     - Orders research outputs based on their overall Altmetric attention score (the number generally shown within Altmetric donuts or other badges).
   * - ``readers``
     - Orders research outputs based on the number of readers. 
   * - ``first_seen``
     - Orders research outputs based on when Altmetric first started tracking mentions.
   * - ``pubdate``
     - Orders by the publication date of the article. This can be approximate; for example, some publishers may not provide an exact publication date, choosing instead to provide only a year or month.


Response object
===============
The Altmetric Details Page API returns JSON. The ``/citations/`` endpoint returns an object with the keys ``query`` and ``results``.

Query object
------------

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

Results object
--------------
A GET request to the ``/citations/`` endpoint returns a JSON object with the following keys.

.. include:: shared/counts-and-citations/counts-and-citations.rst

Cohorts
^^^^^^^

.. include:: shared/counts-and-citations/cohorts.rst

Context
^^^^^^^
Contains details of the Altmetric score and, where possible, provides some context. See :ref:`Breakdown` for a breakdown of context.

.. include:: shared/context_for_score.rst

Breakdown
"""""""""

.. include:: shared/counts-and-citations/breakdown.rst

History
^^^^^^^

.. include:: shared/history.rst

Publisher subjects
^^^^^^^^^^^^^^^^^^

.. include:: shared/counts-and-citations/publisher-subjects.rst

Readers
^^^^^^^

.. include:: shared/readers.rst

Images
^^^^^^

.. include:: shared/images.rst

Example response
================

.. literalinclude:: responses/citations.json
  :language: JSON

Try it yourself
===============
Click on any of the URLs below to view example responses for the listed scenarios. 

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