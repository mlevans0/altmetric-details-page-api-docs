.. list-table:: 
   :widths: 10 10 80
   :header-rows: 1

   * - Key
     - Type
     - Description
   * - ``title``
     - string
     - Title of the publication
   * - ``altmetric_id``
     - number
     - Internal ID associated with the research output. Altmetric IDs are transient and unstable over the medium term.
   * - ``doi``
     - string
     - Relevant DOI.
   * - ``pmid``
     - string
     - Relevant Pubmed Id.
   * - ``pmc``
     - string
     - Relevant Pubmed Central Id.
   * - ``uri``
     - string
     - URI for a captured identifier (e.g https://doi.org/xxx).
   * - ``url``
     - string
     - URL to publication page.
   * - ``isbns``
     - string [] 
     - Relevant ISBN(s).
   * - ``altmetric_jid``
     - string
     - Internal identifier assigned to each journal or collection.
   * - ``handles``
     - string[]
     - Relevant Handle(s).
   * - ``issns``
     - string [] 
     - Relevant ISSN(s).
   * - ``journal``
     - string
     - Name of publication journal.
   * - ``pubdate``
     - number
     - The print date that the publication was published. In Unix.
   * - ``epubdate``
     - number
     - The date that the publication was published electronically. In Unix.
   * - ``published_on``
     - number
     - Returns the ``epubdate`` if it exists on the record -  if not then the ``pubdate`` is returned instead.
   * - ``cohorts``
     - object
     - Groups of users who've mentioned the publication on Twitter.
   * - ``abstract``
     - string
     - Full abstract for the article.
   * - ``abstract_source``
     - string
     - Source for the abstract (e.g PUBMED).
   * - ``authors``
     - string[]
     - Author names.
   * - ``type``
     - string
     - ``dataset`` ``book`` ``article`` ``news`` ``chapter`` ``clinical_trial_study_record``
   * - ``is_oa``
     - boolean 
     - Deprecated.
   * - ``context``
     - object
     - Score in context.
   * - ``cited_by_fbwalls_count``
     - number
     - Number of the pages that have shared on Facebook.
   * - ``cited_by_feeds_count``
     - number
     - Number of blogs that have mentioned the publication.
   * - ``cited_by_gplus_count``
     - number
     - Number of the accounts that have shared on Google+.
   * - ``cited_by_msm_count``
     - number
     - Number of the news sources that have mentioned the publication.
   * - ``cited_by_posts_count``
     - number 
     - A ``post`` is any online document that links to one or more research outputs (i.e. a post is a mention or a group of mentions). This field contains the number of distinct ``posts`` that include one or more mentions of the research outputs in question.
   * - ``cited_by_rdts_count``
     - number
     - Number of Reddit threads posted about this publication.
   * - ``cited_by_tweeters_count``
     - number
     - Number of the twitter accounts that have tweeted this publication.
   * - ``cited_by_videos_count``
     - number
     - Number of the Youtube/Vimeo channels.
   * - ``cited_by_accounts_count``
     - number
     - The sum of all ``cited_by`` entries (profiles per data source).
   * - ``last_updated``
     - number
     - Last time the score changed. In UNIX.
   * - ``score``
     - decimal
     - Current Altmetric Attention Score.
   * - ``history``
     - object
     - History of the Altmetric Attention Score for the research output.
   * - ``added_on``
     - number
     - Date when Altmetric first captured attention. In UNIX.
   * - ``scopus_subjects``
     - string[]
     - Initally imported from Scopus in 2011 (Depricated).
   * - ``subjects``
     - string[]
     - Subjects for journal. Originally enriched from National Academy of Medecine (Depricated).
   * - ``publisher_subjects``
     - object[]
     - Subjects for journal set by the publisher.
   * - ``readers``
     - object
     - Readers.
   * - ``images``
     - object
     - Links to PNG versions of the donut.
   * - ``details_url``
     - string
     - URL to relevant Altmetric Details Page.
   * - ``authors_or_editors``
     - string[]
     - Author and editor names.
   * - ``attribution``
     - string
     - Source of data. For example Google Books.