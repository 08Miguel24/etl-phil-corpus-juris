# **STILL IN PRODUCTION**

*for manual work

extraction tasks:
- *identify all leaf links (links that lead directly to a page)
e.g. sublink 1 leads to page <X1> with content <Y1>, sublink 2 leads to page <X2> with sublink 1, 2, 3, 4, 5 and when each are visited manually leads to a page with content. Therefore leaf nodes are therefore
- *identify element holding most of the important leaf links or identify links with common xpath/css path
- *get this elements xpath/css path by inspecting element
- extract element using xpath/css path, driver.find_element(By.CSS_SELECTOR, link_selector)
- use the element to find all link elements content.find_elements(By.TAG_NAME, "a")
- extract links href attribute using link.get_attribute('href')
- extract links text attribute using link.text
- arrange all extracted link hrefs and link text in dataframe
- save dataframe

- *extract all link text that have commonality
- *paste and enclose in triple quotes """ """
- *by using ctrl-D delete all tabs and whitespaces in order to separate each link text
- 

- *open a leaf link of this dataframe
- *identify element holding most of the content
- *get this elements xpath/css path by inspecting element
- *assume that this xpath/css path of this pages element containing the content is the same for all pages
- iteratively open all link hrefs in dataframe
- iteratively feed xpath/css path to a function to extract the element, driver.find_element(By.CSS_SELECTOR, text_content_selector)
- iteratively use the element extracted to extract all text from it, page_text_content.append(text_content.text)
- arrange all extracted page headers and page contents in a dataframe
- save dataframe

- if a page's content has no common xpath/css path with other pages get the contents full xpaht/css path 
- *extract content manually using library methods/functions e.g. get_content("<xpath string>")
- *manually append to dataframe

transformation tasks:
- remove all consecutive \n and replace with whitespace, re.sub(r"[\n\s]{2,10}", ' ', text_content)
- remove unnecessary phrases re.sub((<some unnecessary phrase 1>|<some unnecessary phrase 2>), '', text_content)
- match all expressions with values 0 to 9 and with at least 2 but not more than 3 digits re.search("(^C|^P)([0-9]{2,3})", content).group()


- probable entities of corpus juris to identify: acts, amounts, citations, companies, constraints, copyright, courts, dates, definitions, distances, durations, geoentities, percents, regulations, trademarks. GET EXAMPLE 

loading tasks:

