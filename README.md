# COVIDminer
An interactive text mining tool to assist curation of SARS-CoV-2 interaction pathways

# Web project
The web project is hosted at http://rupertoverall.net/covidminer

# Issues/feedback
To report bugs, make feature requests etc., please use the [issues tracker](https://github.com/rupertoverall/COVIDminer/issues) associated with this repository.

# About this tool
This project provides access to a database of interactions between genes / proteins, chemicals and biological processes related to the SARS-CoV-2 (COVID-19) virus.

The interactions have been automatically extracted using text mining. The information shown on this site is thus not curated and is intended to be used as an aid to manual literature curation efforts.

The data presented here are based on the [CORD-19](https://www.kaggle.com/allen-institute-for-ai/CORD-19-research-challenge#all_sources_metadata_2020-03-13.csv') dataset, around 30000 abstracts from a [broad PubMed search](https://pubmed.ncbi.nlm.nih.gov/?orig_db=pubmed&term=%22SARS-CoV%22+OR+%222019-nCoV%22+OR+%22HCoV-19%22+OR+%22Wuhan+coronavirus%22+OR+%22Wuhan+seafood+market+pneumonia+virus%22+OR+%22COVID%22), a regularly-updated analysis of full-text manuscripts from the bioRxiv collection ["COVID-19 SARS-CoV-2 preprints from medRxiv and bioRxiv"](https://connect.biorxiv.org/relate/content/181), as well as around 80 full-text manuscripts curated as part of the [COVID-19 Disease Map](https://covid.pages.uni.lu/) project.

Natural language processing (text mining) is performed using the REACH (https://github.com/clulab/reach) reader together with the INDRA (http://www.indra.bio/) toolbox.

This project is run by Rupert Overall (https://rupertoverall.net/, https://twitter.com/rupertoverall)

# Tutorial
A full tutorial can be found at http://rupertoverall.net/covidminer/tutorial

# Mapping
This tool is designed to allow **_rapid assessment of a large body of literature_** &mdash; it does not aim to provide detailed and accurate interaction information. In order to better serve this aim, it was decided to collapse closely-related entities as much as possible. Specifically, all mentions of genes or gene products (RNA, proteins) are mapped to the corresponding gene identifier. In addition, genes and proteins from different organisms (or where the organism is unclear) are mapped to the homologous human gene. This means that potential interactions discovered in closely-related species will be visible when searching for interaction partners of human protein identifiers. The resulting links lead to the underlying literature and it is up to the curator to decide if and how that information fits into their curation scheme.

Likewise, all viral genes/proteins will be mapped to SARS-CoV-2 identifiers. There is currently no uniform mapping scheme available for SARS-CoV-2, but we are actively working on improving this and updated interaction data will be continuously added.

Finally, there are many concepts (particularly biological processes) for which there are no good mappings. Where the natural language processing software has detected an entity that cannot be mapped, it will be presented in the network as plain text. Although there is no detailed metadata for such entities, they can often be informative enough to warrant a closer look at the source manuscript. Often, many separate entities with similar names will be present where they should really be collapsed into one. We are working to improve the mapping resources to remedy this problem.

