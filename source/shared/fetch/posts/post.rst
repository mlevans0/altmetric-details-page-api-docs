.. note::
  For Twitter we will only provide the ``tweet_id`` all other keys are removed.

.. list-table::  
   :widths: 30 10 60
   :header-rows: 1

   * - Key
     - Type
     - Description
   * - ``title``
     - string
     - Title or headline of the mention.
   * - ``url``
     - string
     - Link to the page that mentioned the output.
   * - ``posted_on``
     - string
     - Date and time that the mention was recorded.
   * - ``license``
     - string
     - For Twitter all license types will be set to ``gnip``. For all others available types are ``public``.
   * - ``source``
     - object
     - **Policy only**.
   * - ``geo``
     - object
     - 
   * - ``summary``
     - string
     - A brief summary taken from the mention.
   * - ``image``
     - string
     - A link to the logo associated with the mention source.
   * - ``collections``
     - string []
     - 
   * - ``page_url``
     - string
     - Link to the page that mentioned the output.
   * - ``citation_ids``
     - number[]
     - Collection of Altmetric IDs for outputs that are linked to from this mention.
   * - ``author``
     - object
     - 
   * - ``embed``
     - object
     - 
   * - ``wiki_lang``
     - string
     - **Wikipedia only**. The language code for the version of Wikipedia where the mentioned was retrieved from.
   * - ``tweet_id``
     - string
     - **Twitter only**. The Tweet Id of the tweet.