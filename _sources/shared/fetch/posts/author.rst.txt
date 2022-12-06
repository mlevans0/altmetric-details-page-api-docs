.. note::
  For Twitter we will only provide the ``tweeter_id`` all other keys are removed.

.. list-table:: 
   :widths: 10 10 80
   :header-rows: 1

   * - Key
     - Type
     - Description
   * - ``name``
     - string
     - The name of the author as appears in the mention. Or a link to the mention if not available. 
   * - ``description``
     - string
     - If not an actual person. A description of the source.
   * - ``url``
     - string
     - Link to the homepage/profile associated with the mention.
   * - ``image``
     - string
     - Profile image associated with the author of the mention.
   * - ``id_on_source``
     - string
     - Platform specific unique identifier for the source of the mention. For example a YouTube video Id.
   * - ``facebook_wall_name``
     - string
     - **Facebook only**. The name of the Facebook wall where the mention was retrieved from.
   * - ``tweeter_id``
     - string
     - **Twitter only**. The Twitter Id of the author for the tweet.