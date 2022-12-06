Contains details of the Altmetric score and, where possible, provides some context.

.. list-table:: 
   :widths: 10 10 80
   :header-rows: 1

   * - Key
     - Type
     - Description
   * - ``score``
     - decimal
     - Current Altmetric Attention Score of this article.
   * - ``history``
     - object
     - Allows you to see how the score has developed over time. See :ref:`History` for more information.
   * - ``context_for_score``
     - object 
     - Tells you how this score compares to other scores, for example in the entire database ``all`` or the same journal ``this_journal``. See :ref:`Context for score` for more information.