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
   * - ``pct``
     - number
     - % of publications from this journal with fewer mentions in this time period.
   * - ``higher_than``
     - number
     - Number of publications from this journal with fewer mentions in this time period.

.. note::

   We split the representative sample in percentiles and put the highest score in each 10% into the spark-lines array. Thus the first element of that array is the highest scoring
   article in the sample set, the second element is the highest score in the 90th %ile, the third element in the 80th %ile and so on.