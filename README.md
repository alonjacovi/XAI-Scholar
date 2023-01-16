# XAI-Scholar

Code and data for deriving empirical trends in XAI.

## Sources
Please check the accompanying [Medium blogpost](https://medium.com/@alonjacovi/trends-in-explainable-ai-xai-literature-a1db485e871) and [Arxiv report](http://arxiv.org/abs/2301.05433).

The data was collected as described in the above links. To recap, it is a mix of keyword search via SemanticScholar, and manual curation. The final collection has 5199 papers as of December 31st 2022.

The code used to interface with SemanticScholar uses the unofficial [semanticscholar](https://github.com/danielnsilva/semanticscholar) python library. Install with `pip install semanticscholar`. The plots and graphs use [Seaborn](https://seaborn.pydata.org/) and [GraphOnline](http://graphonline.ru/en/).

## Format
`XAI-Scholar_analysis.ipynb` is a Jupyter Notebook with the code necessary to reproduce the results in the medium/arxiv reports.

`xai-scholar.json` is a json dictionary with 5199 SemanticScholar `paperId` keys.

Each paper has the standard fields given by the SemanticScholar API:
* `paperId`
* `externalIds`
* `url`
* `title`
* `abstract`
* `venue`
* `year`
* `referenceCount`
* `citationCount`
* `influentialCitationCount`
* `isOpenAccess`
* `fieldsOfStudy`
* `s2FieldsOfStudy`
* `tldr`
* `publicationTypes`
* `publicationDate`
* `journal`
* `authors`

Note: Some of the papers are missing some of the fields, or they are marked as empty or `None`. 

The following fields are missing in `xai-scholar.json` and need to be retrieved from SemanticScholar due to their large size (expect around 1 GB without `embedding`):
* `embedding`
* `citations`
* `references`

The code to do so is in the jupyter notebook - but it simply calls `semanticscholar.get_paper(paperId)` for each `paperId`.
