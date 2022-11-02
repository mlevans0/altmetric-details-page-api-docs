Bibliographic metadata about the output requested. You'll find third party identifiers, for example ``doi`` ``pmid`` ``arxiv`` in this object.

.. list-table:: 
   :widths: 10 10 80
   :header-rows: 1

   * - Key
     - Type
     - Description 
   * - ``altmetric_jid``
     - string
     - An internal database identifier for the journal that the article comes from.
   * - ``title``
     - string
     - Title of the publication.
   * - ``doi``
     - string
     - Relevant DOI.
   * - ``pmid``
     - string
     - Relevant Pubmed Id.
   * - ``pmc``
     - string
     - Relevant Pubmed Central Id.
   * - ``handles``
     - string[]
     - Relevant Handle(s).
   * - ``urn``
     - string
     - Relevant URN.
   * - ``ads_id``
     - string
     - Relevant bibcode Id.
   * - ``tq``
     - string
     - 
   * - ``nct_id``
     - string
     - Relevant ClinicalTrials.gov Id.
   * - ``hollis_id``
     - string
     - 
   * - ``hlom_id``
     - string
     - 
   * - ``ssrn``
     - string
     - Relevant Social Science Research Network Id
   * - ``repec``
     - string
     - Relevant RePEc Id.
   * - ``arxiv_id``
     - string
     - Relevant arXiv Id.
   * - ``isbns``
     - string[]
     - Relevant ISBN(s).
   * - ``issns``
     - string[]
     - Relevant ISSN(s).
   * - ``journal``
     - string
     - Name of publication journal.
   * - ``pubdate``
     - date
     - The print date that the publication was published.
   * - ``epubdate``
     - date
     - The date that the publication was published electronically.
   * - ``published_on``
     - date
     - Returns the ``epubdate`` if it exists on the record, if not then the ``pubdate`` is returned instead.
   * - ``type``
     - string
     - ``dataset`` ``book`` ``article`` ``news`` ``chapter`` ``clinical_trial_study_record``
   * - ``abstract``
     - string
     - Full abstract for the article.
   * - ``abstract_source``
     - string
     - Source for the abstract (e.g PUBMED).
   * - ``links``
     - string[]
     - Collection of links that point to all seen versions of this article..
   * - ``first_seen_on``
     - date
     - Date that Altmetric first tracked a share or mention of this article.  
   * - ``issue``
     - string
     - 
   * - ``last_mentioned_on``
     - number
     - Last time the research output was mentioned. In UNIX.
   * - ``pdf_url``
     - string
     - PDF URL to the research output.
   * - ``startpage``
     - string
     - 
   * - ``aggregate_citation_ids``
     - number[]
     - Collection of Altmetric IDs for book chapters.
   * - ``authors``
     - string[]
     - Author names.
   * - ``authors_or_editors``
     - string[]
     - Author and editor names.
   * - ``attribution``
     - string
     - Source of data. For example Google Books.
   * - ``is_oa``
     - boolean
     - Deprecated
   * - ``scopus_subjects``
     - string[]
     - Initally imported from Scopus in 2011 (Depricated).
   * - ``publisher_subjects``
     - object[]
     - Subjects for journal set by the publisher. See :ref:`Publisher subjects`. 
   * - ``subjects``
     - string[]
     - Subjects for journal. Originally enriched from National Academy of Medecine (Depricated).
   * - ``mendeley_url``
     - string
     - URL to the research output in Mendeley.
   * - ``volume``
     - string
     - 
   * - ``book_cover_url``
     - string
     - URL to the book cover.
   * - ``chapters``
     - object
     - See :ref:`Chapters`. 
   * - ``added_on``
     - number
     - Date when Altmetric first captured attention. In UNIX.
   * - ``score``
     - decimal
     - Current Altmetric Attention Score.
   * - ``last_updated``
     - number
     - Last time the score changed. In UNIX.