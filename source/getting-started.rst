Access
******

Authentication
==============
An API key is only required when accessing the **Full Access** endpoint or to remove rate-limiting restrictions enforced on all endpoints. This key is a token that allows our application to verify that
you are authorized to use the API and should be included when making requests. To do this you will need to include a parameter named ``key`` that contains your assigned API key.

For example, if your key was ``xxx-xxx-xxx-xxx`` your request would look like this: ``curl 'http://api.altmetric.com/v1/id/241939?key=xxx-xxx-xxx-xxx'``

For more information regarding obtaining an API key see our :ref:`Licensing` page.

Versioning
==========
To ensure that the code you develop remains functional for as long as possible - endpoints will be assigned new revision numbers if breaking changes are introduced. The current Details Page API version is ``v1``
and should be the version that you should use in production.

You can specify which version of the API to use by changing the base URL for your requests, for example to use ``v1`` you should use ``https://api.altmetric.com/v1/`` and your actual request should look like:

``https://api.altmetric.com/v1/citations/1d``

``https://api.altmetric.com/v1/doi/10.1038/480426a``

Identifiers
***********

Below is a list of our supported identifers.

.. list-table:: 
   :widths: 10 10 80 
   :header-rows: 1

   * - Code
     - Name
     - Description
   * - ``doi``
     - Digital Object Identifier
     - A DOI (Digital Object Identifier) is a unique and persisteant string assigned to online articles, books, and other works. You can read more about DOIs here https://www.doi.org/
   * - ``pmid`` 
     - PubMed Identifier
     - A PMID is the unique identifier number used in PubMed for each article. PMIDs do not change over time or during processing and are never reused. You can read more about PubMed here https://pubmed.ncbi.nlm.nih.gov/
   * - ``handle`` 
     - Handle
     - The Handle System provides a general-purpose global name service enabling secure name resolution over the Internet, designed to enable a broad set of communities to use the technology 
       to identify digital content independent of location. You can read more about Handles here https://www.handle.net/
   * - ``arxiv`` 
     - arXiv Identifier
     - Identifier of a document used in the arXiv pre-print archive. You can read more about arXiv Ids here https://arxiv.org/help/arxiv_identifier
   * - ``ads`` 
     - ADS Bibcode
     - 19 digit identifier which describes a journal article and used to identify literature in the astrophysics data system. You can read more about the ADS Bibcode here https://ui.adsabs.harvard.edu/help/actions/bibcode
   * - ``ssrn``
     - Social Science Research Network identifier
     - Identifer used on the Social Science Research Network repository for preprints. 
   * - ``repec``
     - RePEc ID
     - Identifier for a scholarly article in the RePEc (Research Papers in Economics) database.
   * - ``isbn``
     - International Standard Book Number
     - The ISBN can be either ISBN-10 or ISBN-13 and does not need to be normalized.
   * - ``id``
     - Altmetric Internal Identifier
     - Altmetric IDs are transient and unstable over the medium term. For long term application it is recommended that persistent IDs such as DOIs, arXiv IDs or PMIDs are used instead.
   * - ``nct_id``
     - ClinicalTrials.gov ID
     - Identifier used within the ClinicalTrials.gov database.
   * - ``urn``
     - Uniform Resource Name
     - URNs are globally unique persistent identifiers assigned within defined namespaces so they will be available for a long period of time, even after the resource which they
       identify ceases to exist or becomes unavailable. URNs cannot be used to directly locate an item and need not be resolvable, as they are simply templates that another parser may use to find an item.
       
Limitations
***********

Cross-site scripting
====================
To support older browsers you can use JSONP (JSON with Padding). To do this you will need to include a ``callback`` parameter that contains the name of the Javascript function to invoke when the call returns.

For example: ``https://api.altmetric.com/v1/doi/10.1038/480426a?callback=my_callback``

.. raw:: html

    <script>
      function my_callback(data) {
        alert(`Received ${data.title} from API`);
      }

      function tryIt() {
        let script = document.createElement('script');
        script.src = 'https://api.altmetric.com/v1/doi/10.1038/480426a?callback=my_callback';
        document.body.appendChild(script);
      }
    </script>

    <button class="guilabel" onclick="tryIt()">Try it!</button>
    <br />
    <br />

.. warning:: 
    Altmetric is quite strict about what constitutes as a valid callback - only letters, digits and underscores are allowed.

Rate limiting
=============
Every day the Details Page API handles a large number of requests. To help manage the volume of these requests, limits are placed on the number of requests that can be made from a
specific IP. These limits help us provide a reliable and dependable API service that serves the Altmetric community. 

If you are using the API without a key you can check the ``X-HourlyRateLimit-Limit`` and ``X-DailyRateLimit-Limit`` headers for the current limits. The ``X-HourlyRateLimit-Remaining`` and ``X-DailyRateLimit-Remaining`` headers
will tell you how many calls you have remaining.

When your rate limit has been exceeded, a ``429 'Too many requests'`` error is returned by the API.  When this occurs it is recommended that you examine HTTP headers above and pause requests until
sufficient time has passed. If you find that you frequently hit the rate limit then you might want to consider throttling your requests or purchasing a commercial API key.

Twitter
=======
Due to a contractual agreement that Altmetric has with Twitter, a maximum of 1,500,000 unique tweet IDs can be retrieved in any rolling 30 day period. If your request returns tweet IDs, 
please check the ``X-TweetIDRateLimit-Limit`` and ``X-TweetIDRateLimit-Remaining`` headers to check how close you are to the limit. 

Multiple requests to the same research output will not decrement your remaining limit **unless** it has received new Twitter attention or the request is outside the rolling 30 day window. 
Where the research output has received new attention, the ``X-TweetIDRateLimit-Remaining`` will be reduced by the additional uniqiue tweet IDs and not by the total amount of tweet IDs for the research output.

If you exceed your quota a ``429`` response will be returned along with the message ``Tweet ID rate limit exceeded, please see X-TweetIdRateLimit headers and try again later``.

.. tip::
    If you are using the :ref:`Fetch` endpoint and don't require Twitter information you can use the ``exclude_sources`` query string parameter to remove
    Twitter information from the response.

    For example: ``curl https://api.altmetric.com/v1/fetch/doi/10.1371/journal.pone.0005083?key=xxx-xxx-xxx-xxx&exclude_sources=twitter``

How to obtain additional Twitter information
--------------------------------------------
If you are working on a project that requires information about tweets or tweeters, that is not available via Altmetric's APIs, then you will need to request the  additional data directly from Twitter's own API services. 
You can utilize the Tweet IDs and User IDs that you obtain from Altmetric's APIs to then query the Twitter API for this additional information. If you are using Twitter data for your projects,
please ensure that you are compliant with Twitter's Developer Policy and Twitter's Terms of Service.

To get started you you will first need to apply for developer access to Twitter's APIs `here <https://developer.twitter.com/en/apply-for-access>`_.

Once you have obtained access to Twitter's Developer Portal, you will be able to send requests to the Twitter API. To access detailed information for individual
tweets (which Twitter refers to as "statuses"), you can `query the Twitter API using a single Tweet ID <https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/get-statuses-show-id>`_.

Alternatively, you can request detailed information for a batch of up to 100 tweets at a time `using multiple Tweet IDs <https://developer.twitter.com/en/docs/tweets/post-and-engage/api-reference/get-statuses-lookup>`_.

Hydrate Tweets IDs into actual Tweets
--------------------------------------
For hydration, you can use "Hydrator" – see https://github.com/DocNow/hydrator. This great multi-platform app takes as input a bunch of data (e.g., tweet IDs and your own developer key) and
in turn goes to the Twitter API, retrieving all the tweets that are still available online. It also manages the download process, including download rate limits.

Check the `Content Distribution section on this page <https://developer.twitter.com/en/developer-terms/agreement-and-policy>`_ for more info on Twitter's platform terms and conditions.

.. note::
    When fetching and displaying tweets you should be adhering to Twitter's `display guidelines <https://dev.twitter.com/terms/display-guidelines>`_ and please ensure
    that you are compliant with Twitter's `Terms of Service <https://twitter.com/en/tos>`_ and the `Developer Policy <https://developer.twitter.com/en/developer-terms/policy.html>`_
    when using Twitter data. For further information about Twitter data usage restrictions, please read this `Knowledgebase article <https://help.altmetric.com/support/solutions/articles/6000242073-twitter-data-available-in-altmetric-s-apis-and-data-exports>`_.

News
====
In the United Kingdom, under The Copyright Designs & Patents Act 1988, headlines are copyrighted. To collect the data from UK newspapers Altmetric signed an agreement with the
Newspaper Licensing Authority, which prevents us from including the links and headline to a news story unless the user also has a license from this same agency. As we can't
verify that every person who views our Details Pages has this license we choose not to display the headline and link.  

More information about why we can't display some news mentions is available `here <https://help.altmetric.com/support/solutions/articles/6000241413-unclickable-links-on-a-detail-page>`_.