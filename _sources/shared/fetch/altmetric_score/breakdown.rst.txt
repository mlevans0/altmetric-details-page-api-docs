Available types are ``all`` ``journal`` ``similar_age_3m`` ``similar_age_journal_3m``.

.. list-table:: 
   :widths: 30 10 60
   :header-rows: 1

   * - Key
     - Type
     - Description
   * - ``count``
     - number
     - Number of publications in this journal in this time period.
   * - ``mean``
     - decimal
     - Mean score for publications in this journal in this time period.
   * - ``rank``
     - number
     - Score in context rank within publications in the journal in this time period.
   * - ``total_number_of_other_articles``
     - number
     - Total number of publications in sample size for the journal in this time period.
   * - ``this_scored_higher_than_pct``
     - number
     - % of publications from this journal with fewer mentions in this time period.
   * - ``this_scored_higher_than``
     - number
     - The estimated number of articles that have scored the same or lower than this one.
   * - ``rank_type``
     - string
     - The sample type used to calculate the ``rank``. Prior to 2014 the rank was calculated using an ``approximate`` sample size, now the whole dataset is used. Always set to to ``exact``.
   * - ``sample_size``
     - number
     - The size of the representative sample we use to produce the ``mean`` and other metrics. Duplicates ``total_number_of_other_articles``.
   * - ``percentile``
     - number
     - % of publications from this journal with fewer mentions in this time period. Duplicates ``this_scored_higher_than_pct``. 

.. note::

   We split the representative sample in percentiles and put the highest score in each 10% into the spark-lines array. Thus the first element of that array is the highest scoring
   article in the sample set, the second element is the highest score in the 90th %ile, the third element in the 80th %ile and so on.