# **STILL IN PRODUCTION**

extraction tasks:
- identify all leaf links (links that lead directly to a page)
e.g. sublink 1 leads to page <X1> with content <Y1>, sublink 2 leads to page <X2> with sublink 1, 2, 3, 4, 5 and when each are visited manually leads to a page with content. Therefore leaf nodes are therefore
- identify links with common xpath/css path
- extract links using css xpath/css path
- if a page's content has no common xpath/css path with other pages get thecontents full xpaht/css path and extract ocntent manually using library methods/functions e.g. get_content("<xpath string>")

transformation tasks:
- probable entities of corpus juris to identify: acts, amounts, citations, companies, constraints, copyright, courts, dates, definitions, distances, durations, geoentities, percents, regulations, trademarks. GET EXAMPLE 

loading tasks: