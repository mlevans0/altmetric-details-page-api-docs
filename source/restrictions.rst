Restrictions
============

Twitter
*******
Due to a contractual agreement that Altmetric has with Twitter, a maximum of 1,500,000 tweet IDs can be retrieved in any rolling 30 day period, if your request returns tweet IDs,
please check the ``X-TweetIDRateLimit-Limit`` and ``X-TweetIDRateLimit-Remaining`` headers to check how close you are to the limit. 

.. tip::
    If you are using the :ref:`Fetch` endpoint and don't require Twitter information you can use the ``exclude_sources`` query string paramter to remove Twitter information from the response.

.. note::
    Please ensure that you are compliant with Twitter's `Terms of Service <https://twitter.com/en/tos>`_ and the `Developer Policy <https://developer.twitter.com/en/developer-terms/policy.html>`_
    when using Twitter data. For further information about Twitter data usage restrictions, please read 
    this `knowledgebase article <https://help.altmetric.com/support/solutions/articles/6000242073-twitter-data-available-in-altmetric-s-apis-and-data-exports>`_.

News
****
In the United Kingdom, under The Copyright Designs & Patents Act 1988, headlines are copyrighted. To collect the data from UK newspapers Altmetric signed an agreement with the
Newspaper Licensing Authority, which prevents us from including the links and headline to a news story unless the user also has a license from this same agency. As we can't
verify that every person who views our Details Pages has this license we choose not to display the headline and link.  

More information about why we can't display some news mentions is available `here <https://help.altmetric.com/support/solutions/articles/6000241413-unclickable-links-on-a-detail-page>`_.