Provides the number of mentions and unique authors in each relevant source type.

.. list-table:: 
   :widths: 10 10 80
   :header-rows: 1

   * - Key
     - Type
     - Description
   * - ``unique_users_count``
     - number
     - Number of unique users.
   * - ``unique_users``
     - string[]
     - User IDs associated with the posts.
   * - ``posts_count``
     - number
     - Total number of posts. 

.. note::
  The same user could blog, tweet or otherwise share the same article more than once, so ``posts_count`` can be greater than ``unique_users_count``. 