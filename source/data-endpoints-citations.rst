Citations
*********
List research outputs with activity in a given timeframe (see the ``timeframe`` parameter in the table below for supported values).

Parameters
==========

.. list-table:: 
   :widths: 20 10 35 35
   :header-rows: 1 

   * - Parameter
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

Citations object
----------------
A GET request to the ``/citations/`` endpoint returns a JSON object.

.. csv-table::
   :file: tables/counts-and-citations-field-glossary.csv
   :widths: 30 10 60
   :header-rows: 1

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

    <button class="guilabel" onclick="renderTopTen()">Try it!</button>

    <br />
    <br />