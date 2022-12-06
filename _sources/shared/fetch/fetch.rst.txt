.. list-table:: 
   :widths: 10 10 80
   :header-rows: 1

   * - Keys
     - Type
     - Description
   * - ``altmetric_id``
     - number
     - Internal ID associated with the research output. Altmetric IDs are transient and unstable over the medium term. 
   * - ``counts``
     - object
     - Provides the number of mentions and unique authors in each relevant source type - for example ``blogs`` ``twitter`` ``news`` as well as reference manager reader counts
       where available. See :ref:`Counts` for more information.
   * - ``citation``
     - object
     - Bibliographic metadata about the output requested. You'll find third party identifiers for example ``doi`` ``pmid`` ``arxiv`` in this object. See :ref:`Citation`  for more information.
   * - ``altmetric_score``
     - object
     - Contains details of the Altmetric score and where possible provides some context. See :ref:`Altmetric Score`  for more information.
   * - ``demographics``
     - object
     - Altmetric categorizes users from some sources based on their posting history and profile information. Counts for each category are included in this section along with geo-location data. See :ref:`Demographics`.
   * - ``posts``
     - object
     - Contains all the recorded mention data categorized by the attention source. See :ref:`Posts`  for more information.
   * - ``score``
     - decimal 
     - Contains details of the Altmetric score and where possible provides some context.
   * - ``images``
     - object
     - Links to PNG versions of the donut. See :ref:`Images`  for more information.