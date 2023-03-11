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

- probable entities of corpus juris to identify: CITATION, AMOUNT, COMPANY, CONSTRAINT, COPYRIGHT, COURT, DATE, DEFINITION, DISTANCE, DURATION, GEOENTITY, PERCENT, REGULATION, TRADEMARK, JUDGEMENT, GAZETTE, PROCEEDINGS, ARTICLE, SECTION, CLAUSE, PARAGRAPH, DEFENDANT, PROSECUTOR, APPEAL, APPELANT, PLAINTIFF, INVOLVED ENTITY, ADVOCATE, LEARNED COUNSEL, ROLE, JUDGE, OFFENCE, ACCUSATION, OBJECTION, JURISDICTION, PENALTY, COMPENSATION, EVIDENCE, EVIDENCE DESCRIPTION, ACT, CIRCULAR, SERIES, CASE, GENERAL REGISTRY NUMBER, PETITION, RULE, ORGANIZATION

Petitioner: Another word for plaintiff, the person starting the lawsuit. Plaintiff: The person who sues or starts a civil case, also called the petitioner or the complainant.

- upload or indicate all possible entities in the web app, expertise of legal practitioner would be better
- convert page text content into individual text files
- download git repo or use web app to annotate text files
- use text files in web app and start annotating all text files with proper entity types
- save dataset 


- create system architecture for dealing with the raw text content in .txt files, 
but since we are to annotate the corpus juris manually and all of it, we won't need a NER model anymore to identify the entities since we won't need to identify anymore entities in other documents that revolve around this body of law since we annotated it all already. The next process instead would be to use these identified entieis in the text and createa a knowledge graph using God knows what


concepts:
Judgement: title(STRING), last_updated(STRING),  first_trial_date(DATE), decision_date(DATE)
Gazette: title(STRING), published_date(DATE)
Proceedings: proceeding_date(DATE)
Article: title(STRING), category(STRING), act_title(STRING),amendment(STRING)
Section: title(STRING)
Clause: _begin(STRING), clause_text(STRING)
Paragraph: _begin(STRING), paragraph_text(STRING)
Court: name(STRING), location(STRING)
Defendant: name(STRING), gender(STRING), age(NUMBER)
Prosecutor: name(STRING), gender(STRING), age(NUMBER)
Appeal: appealed_by(STRING), description(STRING)
Appellant: name(STRING), gender(STRING), age(NUMBER)
Plaintiff: name(STRING), gender(STRING), age(NUMBER)
Involved_entity: organization(STRING)
Advocate: name(STRING), gender(STRING)
Learned_counsel: name(STRING), gender(STRING)
Role: role_name(STRING)
Judge: name(STRING), gender(STRING)
Offence: title(STRING), description(STRING)
Accusation:title(STRING)
Objection: objected_by(STRING), type(STRING)
Testify: description(STRING), testified_by(STRING)
Jurisdiction: title(STRING), Jurisdiction_description(STRING)
Penalty: title(STRING), penalty_description(STRING)
Compensation: amount(NUMBER), description(STRING)
Evidence: name(STRING), source(STRING), evidence_description(STRING)
relation: 
isa:Involved_entity:Advocate
isa:Involved_entity:Judge
isa:Involved_entity:Defendant
isa:Involved_entity:Prosecutor
isa:Involved_entity:Learned_counsel
isa:Involved_entity:Appellant
isa:Prosecutor:Appellant
isa:Advocate:Defendant
isa:Advocate:Prosecutor
isa:Paragraph:Clause
isa:Paragraph:Offence
partof:Jurisdiction:Penalty
partof:Jurisdiction:Compensation
partof:Judgement:Paragraph
partof:Judgement:Proceedings
partof:Article:Section
partof:Section:Clause
hasa:Role:Advocate
hasa:Role:Learned_counsel
hasa:Gazette:Judgement
isbasedon:Jurisdiction:Evidence
isbasedon:Penalty:Offence
isbasedon:Evidence:Testify
responsiblefor:Jurisdiction:Judge
responsiblefor:Objection:Advocate
responsiblefor:Accusation:Advocate
responsiblefor:Judgement:Court
responsiblefor:Offence:Involved_entity
responsiblefor:Testify:Plaintiff
responsiblefor:Evidence:Plaintiff
responsiblefor:Evidence:Learned_counsel
responsiblefor:Appeal:Advocate
citing:Judgement:Clause
citedby:Clause:Judgement
accusedof:Offence:Defendant
accusedof:Penalty:Prosecutor
accusedof:Penalty:Defendant
functional:Paragraph:Gazette:N:1:inGazette
functional:Clause:Section:N:1:inSection
functional:Section:Article:N:1:inArticle
functional:Offence:Accusation:N:1:inAccusation
functional:Penalty:Jurisdiction:N:1:inJurisdiction
functional:Advocate:Judgement:N:1:inJudgement
functional:Defendant:Judgement:N:1:inJudgement
functional:Plaintiff:Judgement:N:1:inJudgement
functional:Evidence:Judgement:N:1:inJudgement
functional:Prosecutor:Judgement:N:1:inJudgement
functional:Judge:Judgement:1:1:inJudgement
functional:Article:Judgement:N:1:inJudgement
functional:Proceedings:Judgement:N:1:inJudgement
functional:Learned_counsel:Advocate:N:1:underSupervisionOfAdvocate
functional:Objection:Advocate:N:1:objectionsInCourt

concepts:
Judgement: title(STRING), last_updated(STRING),  first_trial_date(DATE), decision_date(DATE)
Gazette: title(STRING), published_date(DATE)
Proceedings: proceeding_date(DATE)
Article: title(STRING), category(STRING), act_title(STRING),amendment(STRING)
Section: title(STRING)
Clause: _begin(STRING), clause_text(STRING)
Paragraph: _begin(STRING), paragraph_text(STRING)
Court: name(STRING), location(STRING)
Defendant: name(STRING), gender(STRING), age(NUMBER)
Prosecutor: name(STRING), gender(STRING), age(NUMBER)
Appeal: appealed_by(STRING), description(STRING)
Appellant: name(STRING), gender(STRING), age(NUMBER)
Plaintiff: name(STRING), gender(STRING), age(NUMBER)
Involved_entity: organization(STRING)
Advocate: name(STRING), gender(STRING)
Learned_counsel: name(STRING), gender(STRING)
Role: role_name(STRING)
Judge: name(STRING), gender(STRING)
Offence: title(STRING), description(STRING)
Accusation:title(STRING)
Objection: objected_by(STRING), type(STRING)
Testify: description(STRING), testified_by(STRING)
Jurisdiction: title(STRING), Jurisdiction_description(STRING)
Penalty: title(STRING), penalty_description(STRING)
Compensation: amount(NUMBER), description(STRING)
Evidence: name(STRING), source(STRING), evidence_description(STRING)
relation: 
isa:Involved_entity:Advocate
isa:Involved_entity:Judge
isa:Involved_entity:Defendant
isa:Involved_entity:Prosecutor
isa:Involved_entity:Learned_counsel
isa:Involved_entity:Appellant
isa:Prosecutor:Appellant
isa:Advocate:Defendant
isa:Advocate:Prosecutor
isa:Paragraph:Clause
isa:Paragraph:Offence
partof:Jurisdiction:Penalty
partof:Jurisdiction:Compensation
partof:Judgement:Paragraph
partof:Judgement:Proceedings
partof:Article:Section
partof:Section:Clause
hasa:Role:Advocate
hasa:Role:Learned_counsel
hasa:Gazette:Judgement
isbasedon:Jurisdiction:Evidence
isbasedon:Penalty:Offence
isbasedon:Evidence:Testify
responsiblefor:Jurisdiction:Judge
responsiblefor:Objection:Advocate
responsiblefor:Accusation:Advocate
responsiblefor:Judgement:Court
responsiblefor:Offence:Involved_entity
responsiblefor:Testify:Plaintiff
responsiblefor:Evidence:Plaintiff
responsiblefor:Evidence:Learned_counsel
responsiblefor:Appeal:Advocate
citing:Judgement:Clause
citedby:Clause:Judgement
accusedof:Offence:Defendant
accusedof:Penalty:Prosecutor
accusedof:Penalty:Defendant
functional:Paragraph:Gazette:N:1:inGazette
functional:Clause:Section:N:1:inSection
functional:Section:Article:N:1:inArticle
functional:Offence:Accusation:N:1:inAccusation
functional:Penalty:Jurisdiction:N:1:inJurisdiction
functional:Advocate:Judgement:N:1:inJudgement
functional:Defendant:Judgement:N:1:inJudgement
functional:Plaintiff:Judgement:N:1:inJudgement
functional:Evidence:Judgement:N:1:inJudgement
functional:Prosecutor:Judgement:N:1:inJudgement
functional:Judge:Judgement:1:1:inJudgement
functional:Article:Judgement:N:1:inJudgement
functional:Proceedings:Judgement:N:1:inJudgement
functional:Learned_counsel:Advocate:N:1:underSupervisionOfAdvocate
functional:Objection:Advocate:N:1:objectionsInCourt

concepts:
Courts: locatedAt(STRING)
Government: governmentName(STRING)
Individual: individualName(STRING)
Organization: organizationName(STRING)
State: stateName(STRING)
Case: hasCaseNumber(LITERAL), hasCaseName(STRING)
Court Decision: hasCourtDecision(DATETIME)
Judgement: hasJudgement(STRING)
Order: hasOrder(STRING)
Thing: topDataProperty(LITERAL)
relations:
isa:Criminal_Courts:Chief_Meterpolitan_Court
isa:Criminal_Courts:Metropolitan_Magistrate_Courts
isa:Criminal_Courts:Sessions_Court
isa:Criminal_Courts:Judicial_Magistrate_Court_(First_Class)
isa:Criminal_Courts:Judicial_Magistrate_Court_(Second_Class)
isa:Civil_Courts:Sub_Court
isa:Civil_Courts:City_Civil_Courts
isa:Civil_Courts:District_Court
isa:Civil_Courts:Courts_of_Smaller_Causes
isa:Civil_Courts:_Munsif_Court
isa:Civil_Courts:Principal_Junior_Civil_Court
isa:Case_Type:Criminal_Courts
isa:Case_Type:Civil
isa:Case_Type:Civil_Courts
isa:Case_Type:Criminal
isa:Jurisdiction:Writ_Jurisdiction
isa:Jurisdiction:Original_Jurisdiction
isa:Jurisdiction:Advisory_Jurisdiction
isa:Jurisdiction:Review_Jurisdiction
isa:Jurisdiction:Appellant_Jurisdiction
hasReviewJurisdiction:Review_Jurisdiction:Apex_Court
hasAdvisoryJurisdiction:Advisory_Jurisdiction:Apex_Court
isa:Courts:Apex_Court
isa:Courts:High_Court
isa:Courts:Metropolitan_Court
isa:Courts:Tribunals
isa:Courts:District_Courts
isa:Non-Legal_Participants:Appellant
isa:Non-Legal_Participants:Plaintiff
isa:Non-Legal_Participants:Petitioner
isa:Non-Legal_Participants:Witness
isa:Non-Legal_Participants:Rspondent
isa:Non-Legal_Participants:Accused
hasNonLegalParticipants:Non-Legal_Participants:Case
hasParticipantType:Non-Legal_Participants:Participants
isa:Participants:State
isa:Participants:Government
isa:Participants:Group
hasIndividuals:Individual:Group
isa:Participants:Individual
isa:Participants:Organization
isa:Location:State
isa:Location:Country
isa:Location:Taluka
isa:Location:District
isa:Location:Place
hasEvidenceLocation:Place:Evidence
hasLocation:Location:Courts
hasCourts:Courts:Case
hasAuthor:Author:Case
caseBelongsToType:Case_Type:Case
hasPrecedentCase:Precedent_Case:Case
isA:Case:Precendent_Case
hasCourtDecision:Court_Decision:Case
isa:Court_Decision:Judgement
isa:Court_Decision:Order
hasLegalParticipants:Legal_Participants:Case
isa:Legal_Participants:Judge
isa:Legal_Participants:Investigator
isa:Legal_Participants:Solicitor
documentType:Court_Judgements:Case
isa:Documents:Court_Judgements
isa:Documents:Appeal
isa:Documents:FIR
isa:Documents:Petition
isa:Documents:Others
hasActs:Acts:Case
hasBench:Bench:Case
isa:Bench:Special_Bench
isa:Bench:Tribunal_Bench
isa:Bench:Division_Bench
isa:Bench:Larger_Bench
isa:Bench:Single_Judge
hasEvidences:Evidence:Case
hasWritJurisdiction:Thing:Thing
topObjectProperty:Thing:Thing

concepts
person:title(STRING)
name:title(STRING)
organization:title(STRING)
academic_degree:title(STRING)
award_received:title(STRING)
candidacy_in_election:title(STRING)
educated_at:title(STRING)
employer:title(STRING)
first_name:title(STRING)
gender:title(STRING)
honorific:title(STRING)
ideology:title(STRING)
instance_of:title(STRING)
language:title(STRING)
last_name:title(STRING)
nationality:title(STRING)
occupation:title(STRING)
place_of_birth:title(STRING)
political_party:title(STRING)
position_held:title(STRING)
religion:title(STRING)
sexual_orientation:title(STRING)
location:title(STRING)
state:title(STRING)
country:title(STRING)
identity:stitle(STRING)
twitter_username:title(STRING)
web_page:title(STRING)
wikidata_qid:title(STRING)
work_location:title(STRING)
attribute:title(STRING)
relationship:title(STRING)
relation
isa:twitter_username:identity
isa:wikidata_qid:identity
functional:name:attribute:N:1:hasName
functional:academic_degree:attribute:N:1:inAttribute
functional:candidacy_in_election:person:N:1:inPerson
functional:first_name:name:1:1:hasFirstName
functional:gender:attribute:1:1:hasGender
functional:honorific:person:1:1:hasHonorific
functional:ideology:person:N:1:inPerson
functional:instance_of:person:1:1:hasInstanceType
functional:language:person:N:1:inPerson
functional:last_name:name:1:1:hasLastName
functional:nationality:attribute:1:1:hasNationality
functional:occupation:person:N:1:inPerson
functional:place_of_birth:attribute:1:1:hasPlaceOfBirth
functional:academic_degree:educated_at:1:1:inEducatedAt
functional:employer:organization:N:1:inOrganization
functional:political_party:organization:N:1:inOrganization
functional:position_held:organization:1:N:inOrganization
functional:person:organization:N:1:hasAffiliation
functional:religion:person:1:1:hasReligion
functional:sexual_orientation:attribute:1:1:hasSexualOrientation
functional:state:location:1:1:hasState
functional:country:location:1:1:hasCountry
functional:identity:person:1:1:hasIdentity
functional:twitter_username:person:1:1:hasTwitterUserName
functional:web_page:person:1:1:hasWebPage
functional:work_location:location:1:1:hasWorkLocation
functional:educated_at:organization:N:1:inOrganization
functional:person:person:N:N:haveAcquaintance
functional:location:person:1:1:hasLocation
functional:attribute:person:N:1:hasAttributes
functional:ideology:political_party:N:1:hasIdeology
functional:ideology:religion:N:1:hasIdeology


loading tasks:

