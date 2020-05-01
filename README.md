# covid19-miner
An interactive text mining tool to assist curation of Sars-CoV-2 interaction pathways

# Web project
The web project is hosted at http://rupertoverall.net/covid19/miner

# Issues/feedback
To report bugs, make feature requests etc., please use the issues tracker associated with this repository.

# About this tool
This project provides access to a database of interactions between genes / proteins, chemicals and biological processes related to the SARS-Cov2 (COVID-19) virus.

The interactions have been automatically extracted using text mining. The information shown on this site is thus not curated and is intended to be used as an aid to manual literature curation efforts.

The data presented here are based on the CORD-19 dataset. We are also adding a daily-updated analysis of manuscripts from the bioRxiv collection "COVID-19 SARS-CoV-2 preprints from medRxiv and bioRxiv".

Natural language processing (text mining) is performed using the REACH (https://github.com/clulab/reach) reader together with the INDRA (http://www.indra.bio/) toolbox.

This project is run by Rupert Overall (https://rupertoverall.net/, https://twitter.com/rupertoverall)

Please note that this web tool is still under development and the site will change often.

# Tutorial
## Search
Start in the Search tab and type the name of a gene/protein or biological process of interest into the search box. Click on the magnifying glass icon or hit enter to confirm. The database will be searched for your term and, if found, the corresponding entry will be returned, together with all of the entities that are connected to it, as a graphically-displayed network. If your search term matches several entries in the database, they will be all returned in a list and you can select the one that best corresponds to your intended search. If there is no match in the database, then nothing is returned. Not all proteins etc. have been mentioned in the COVID-19 literature, so many of your favourite genes will not be found.

## Navigate the network
Once you have loaded a network, you will be automatically switched to the Graph tab where there are some tools for navigating the network graph. For some queries, there may be very many entities (nodes) and it can be confusing to see what's going on. Using the buttons in the Zoom group, you can increase or reduce node size so that the nodes and their labels don't overlap so much and become more readable. Using the buttons in the Simplify group, you can collapse multiple edges (the links between nodes) into a single edge . The width of the connection lines will now reflect how many replicate edges there are. Replication of edges occurs when more than one manuscript provides evidence of the same interaction — so this can be a hint that the interaction might be real and/or important (remember this is automated text mining and includes much non-peer-reviewed literature). In order to follow up the links to individual literature sources, you will need to 'unsimplify' the edge again so that all of the replicate interactions are shown — they will all have different literature links. To better focus on a particular interaction, or subset of interactions, you can click on several nodes while holding down the <shift> key. This will select (highlight) the nodes. The Show/Hide button (with the yellow nodes) will now hide the non-selected nodes so you can focus on them. You can re-run the layout to fit this new sub-network to the screen area (see below) and perform all other operations. Clicking on the Show/Hide button again will reveal the rest of the network again. The buttons in the Layout group will re-run the layout algorithm to place the nodes in a particular way and fi the network to the available space on the screen. The default 'force-directed' layout will push the nodes apart to make them as far apart as possible (and involves a random stem so the layout will be different each time you run it), whereas the 'grid' layout places nodes on a grid, which can be neater, but makes the relationship between nodes a bit less obvious.

## Elements
The elements tab is used to show detailed information about the currently-selected graph element (a node or an edge). If you click on a node or an edge, you will be automatically switched to this tab (you can always switch manually between tabs at any time). For a node, the node name and class (whether it is a gene/protein, a chemical, a biological process, or some other unknown type) is shown as well as its accession code in the most appropriate database. The entry in the relevant database is loaded and shown in the information field below. To load this page in a new browser tab, click the 'linkout' arrow next to the Element info text. For some entities, there is no mapping to an external database, so this information is not available. Please see the notes about mapping below. For an edge, the information shown includes the source and target nodes and whether it is a positive or negative interaction. Positive interactions (red lines) are shown as arrows in the graph, whereas lines representing negative interactions (in blue) end with a 'T'. Interactions depicted with broken lines are derived from non-peer-reviewed preprints. Please note that for collapsed edges (see Simplify above), both arrow endings may be shown; this happens because the arrows are simply drawn on top of each other and different literature sources can propose different interactions between the same entities.

## Export
It is possible to export an interesting network either as a CSV file (comma-delimited text file that can also be opened in Excel) containing a table all of the interactions, as a JSON file describing the underlying Cytoscape.js graph, or as a screenshot of the current graph window (in PNG format).

# Mapping
This tool is designed to allow rapid assessment of a large body of literature &mdash; it dos not aim to provide detailed and accurate interaction information. In order to better serve this aim, it was decided to collapse closely-related entities as much as possible. Specifically, all mentions of genes or gene products (RNA, proteins) are mapped to the corresponding gene identifier. In addition, genes and proteins from different organisms (or where the organism is unclear) are mapped to the homologous human gene. This means that potential interactions discovered in closely-related species will be visible when searching for interaction partners of human protein identifiers. The resulting links lead to the underlying literature and it is up to the curator to decide if and how that information fits into their curation scheme.

Likewise, all viral genes/proteins will be mapped to SARS-Cov-2 identifiers. There is currently no uniform mapping scheme available for SARS-CoV-2, but we are actively working on improving this and updated interaction data will be continuously added.

Finally, there are many concepts (particularly biological processes) for which there are no good mappings. Where the natural language processing software has detected an entity that cannot be mapped, it will be presented in the network as plain text. Although there is no detailed metadata for such entities, they can often be informative enough to warrant a closer look at the source manuscript. Often, many separate entities with similar names will be present where they should really be collapsed into one. We are working to improve the mapping resources to remedy this problem.

