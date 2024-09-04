# OntoGenix Evaluation

This repository describes the evaluation of OntoGenix in the development of ontologis related to commercial activities. For this purpose, six ontologies have been developed with ontologies for six datasets. An ontology for each dataset has also been developed by humans. In this evaluation we have compared the ontologies developed by OntoGenix and the ones developed by humans.

# The datasets

We have evaluated OntoGenix by applying it to a series of Kaggle datasets related to commercial activities of organizations, which are described next:
* [Airlines Customer satisfaction](https://www.kaggle.com/datasets/sjleshrac/airlines-customer-satisfaction): customers who have already flown with them, including the feedback of the customers on various contexts
* [Amazon Ratings](https://www.kaggle.com/datasets/skillsmuggler/amazon-ratings): Customer reviews and ratings of Beauty related products sold on their website.
* [BigBasket Products](https://www.kaggle.com/datasets/chinmayshanbhag/big-basket-products): Products listed on the website of online grocery store Big Basket
* [Brazilian e-commerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce): Brazilian e-commerce public dataset of orders made at Olist Store.
* [Customer complaint](https://www.kaggle.com/datasets/utkarshx27/consumer-complaint): Collection of complaints about consumer financial products
* [E-commerce](https://www.kaggle.com/datasets/carrie1/ecommerce-data): Transactions for a UK-based and registered non-store online retail.


## The OntoGenix and the human ontologies 

The next table links the ontologies used in the evaluation. 

| Dataset | Human generated ontology | LLM generated ontology |
| ------- | ----------------------- | --------------------- |
| [Airline customer satisfaction](https://www.kaggle.com/datasets/sjleshrac/airlines-customer-satisfaction) | [AirlinesCustomerSatisfaction_ontology_human.owl](ontologies/AirlinesCustomerSatisfaction_ontology_human.owl) | [AirlinesCustomerSatisfaction_ontology_LLM.owl](ontologies/AirlinesCustomerSatisfaction_ontology_LLM.owl) |
| [Amazon rating](https://www.kaggle.com/datasets/skillsmuggler/amazon-ratings) | [AmazonRatings_ontology_human.owl](ontologies/AmazonRatings_ontology_human.owl) | [AmazonRatings_ontology_LLM.owl](ontologies/AmazonRatings_ontology_LLM.owl) |
| [BigBasketProducts](https://www.kaggle.com/datasets/chinmayshanbhag/big-basket-products) | [BigBasketProducts_ontology_human.owl](ontologies/BigBasketProducts_ontology_human.owl) | [BigBasketProducts_ontology_LLM.owl](ontologies/BigBasketProducts_ontology_LLM.owl) |
| [Brazilian e-commerce](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) | [BrazilianEcommerce_ontology_human.owl](ontologies/BrazilianEcommerce_ontology_human.owl) | [BrazilianEcommerce_ontology_LLM.owl](ontologies/BrazilianEcommerce_ontology_LLM.owl) |
| [Customer complaints](https://www.kaggle.com/datasets/utkarshx27/consumer-complaint) | [CustomerComplaint_ontology_human.owl](ontologies/CustomerComplaint_ontology_human.owl) | [CustomerComplaints_ontology_LLM.owl](ontologies/CustomerComplaint_ontology_LLM.owl) |
| [eCommerce](https://www.kaggle.com/datasets/carrie1/ecommerce-data) | [eCommerce_ontology_human.owl](ontologies/eCommerce_ontology_human.owl) | [eCommerce_ontology_LLM.owl](ontologies/eCommerce_ontology_LLM.owl) |


## Evaluation method

The evaluation has consisted in generating information from both qualitative and a quantitative perspectives for the comparative assessment of the human and OntoGenix ontologies. Two humans played the role of ontology engineer, each of them manually developing three ontologies. Both humans had an experience of at least 5 years in the development of ontologies from different domains. The development of both types of ontologies was independent, and the people involved in both processes was different. 


The qualitative assessment was done by a third ontology engineer with more than 10 years of experience in ontology development, by manually assessing the two ontologies developed for each dataset.

The quantitative assessment has been done by using ontology evaluation automated tools.  The objective of this evaluation is to compare the ontologies developed by the human and by OntoGenix  and to study whether the modelling style is consistent across datasets. 

* Calculating and comparing the values of the 19 quality metrics included in the [OQuaRE ontology evaluation framework](https://semantics.inf.um.es/oquare). OQuaRE generates two types of values for a metric. The first value is the raw value, whose range depends on the nature of each metric. The second value is the scaled value or quality score, which is a discrete value in the range 1-5, where 1 is the lowest score, and 5 is the highest one. It should be noted that not always a high raw value of a metric is desired from a quality perspective. Therefore, higher raw values of metrics may be associated with lower scaled ones. An example of such situation is TMOnto, which stands for the ratio of classes with multiple ancestors. We have generated a file with the [raw and scaled values of the OQuaRE metrics](oquare/metrics.xlsx).  In order to generate the OQuaRE scores we have used the [GitHub action available for OQuaRE](https://github.com/tecnomod-um/oquare-metrics), whose results are available in the [oquare folder](https://github.com/tecnomod-um/OntoGenixEvaluation/tree/main/oquare/results/ontologies), there is one folder per ontology. For each ontology there is one *README.md* file which shows all the figures available in the *img* folder. OQuaRE outputs the values of the metrics in an XML file which is also provided in the *metrics* folder. The LLM ontologies are in RDF/XML format despite OntoGenix generates them in Turtle. The files have been transformed into RDF/XML using the [EasyRDF Converter](https://www.easyrdf.org/converter). The reason for this conversion is that OQuaRE input ontologies must be in this format. 

* Finding potential modelling errors with the [Ontology Pitfall Scanner (OOPS!)](https://oops.linkeddata.es). The PNG and RDF files generated by the tool are available in a [specific repository](https://github.com/tecnomod-um/OntoGenixEvaluation/tree/main/oops). OOPS! checks for [41 types of pitfalls in ontologies](https://oops.linkeddata.es/catalogue.jsp).

* OntoGenix aims at saving time in the development of the ontologies. We have measured the time spent in (1) the development of the ontology from scratch, and (2) starting with the OntoGenix ontology and transforming it to the human one. The development from scratch requires the following activities: (1) analysis of the CSV data; and (2) construction of the ontology. The development from the OntoGenix ontologies requires the following activities: (1) analysis of the CSV; (2) revision of the ontology generated with OntoGenix, which includes generating the ontology with OntoGenix; and (3) development of the human ontology from the OntoGenix. The analysis of the CSV data is done in both cases, so it will not be considered in this analysis. Therefore, the time from scratch will be the time spent by the human in the modeling of the ontology, and the time starting from the OntoGenix ontology will include the time of running and reviewing the OntoGenix result, and modifying that ontology. Once both times are available, the time saved in absolute and relative terms is calculated. The reconstruction of the human ontology was done by the ontologists involved in the development of the human ontologies. Besides, a qualitative rating to the effort needed to transform the OntoGenix ontology into the human ontology was assigned in the range 1-5: 1 (very little effort), 2 (little effort), 3 (moderate effort), 4 (high effort), 5 (very high effort). This assessment was done by the ontologists involved in the development and evaluation of the human and the OntoGenix ontologies.


## Results of the Quantitative Evaluation

### OQUARE

* [Raw and scaled values of the OQuaRE metrics](oquare/metrics.xlsx)

In OQuaRE, each ontology is assigned with a 1-5 score for each one of the 19 metrics.

For simplicity, the next table only shows  metrics for which different scores are obtained by OntoGenix and the human ontologies. The number in brackets represents the number of metrics for which both ontologies get the same score, ranging from 10 to 17 (out of 19).

The next table shows for which metrics the LLM and the human ontologies got different scores for the metrics. A metric in a cell means which ontology got the higher score. We also show in the table who developed each ontology.


| Dataset | LLM ontology | Human  ontology | Ontologist |
| ------- | ----------------------- | --------------------- | ---------------------| 
| Airlines Customer satisfaction (13)  | RFCOnto, NOMOnto | WMCOnto2, NOCOnto, DITOnto, LCOMOnto | A |
| Amazon Ratings (10) | RROnto, NOMOnto, INROnto | WMCOnto2, TMOnto2, TMOnto, PROnto, DITOnto, ANOnto | A|
| BigBasket Products  (17) | ANOnto | NOCOnto | B|
| Brazilian e-commerce (12)  | RROnto, RFCOnto, NOMOnto, NOCOnto, CROnto, AROnto | PROnto | B|
| Customer complaint  (12)| NOCOnto,CROnto, AROnto, ANOnto | WMCOnto2, NOMOnto, DITOnto | A|
| E-commerce  (13) | RROnto, RFCOnto, NOMOnto, NOCOnto, ANOnto | PROnto | B|


* The LLM ontologies obtain higher scores for RFCOnto (number of usages of object, datatype properties and superclasses), NOMOnto (average number of properties per class), RROnto (ratio of taxonomic relations and object properties) and ANOnto (ratio of annotations). These metrics are mainly related with the richness in content.

* The human ontologies obtain higher scores for WMCOnto2 (number of paths in the ontology), DITOnto (depth of the hierarchy) and PROnto (ratio of properties). These metrics are mainly related with the complexity of the structure of the ontology.

* The human ontologies developed by A tend to have more metrics with higher scores than the LLM, whereas the opposite happens for B. 

The results shows that there are punctual differences for other metrics. It is worthy noting that NOCOnto gets a higher score for 3 LLM ontologies and for 2 human ones. This metric is related to the number of subclasses and the number of non-leaf classes, thus also related to the complexity of the structure of the ontology. As mentioned, the metrics scores are in the range 1-5. If we only consider those metrics whose values differ in at least 2 units in the scale (for instance 5 and 3), the LLM would have higher scores for the following metrics: ANOnto (BigBasket, Customer, eCommerce), RFCOnto(Brazilian, eCommerce), AROnto (Brazilian, Customer), NOMOnto (Brazilian), NOCOnto (Brazilian). 
Consequently, the most significant differences are found for the Brazilian and eCommerce datasets. These are domains modeled by ontologist B. On the contrary, 2 units in the scale higher scores would be obtained by the human ontologies for  WMCOnto (Airlines), TMOnto2 (Amazon) and ANOnto (Amazon).  Airlines and Amazon are domains modeled by ontologist A.

### OOPS!

[Data file with the pitfalls found for each ontology](oops/oops-summary.xlsx)

OOPS! identified 59 (LLM) and 38 (human) occurrences of pitfalls: critical (11/4), important (22/13) and minor (26/21). The next table provides a summary of the occurrences by dataset. The LLM ontologies have more pitfalls for every dataset. The 38 occurrences of pitfalls in human ontologies are associated with 13 different pitfalls, and the 59 of the LLM ontologies with 15 different pitfalls (out of 41 pitfalls included in the catalog). 

|                     | **Human** | **LLM** | **Ontologist** |
|---------------------|--------------|--------------|---------------------|
| **Airlines**   | 4            | 13           | A                   |
| **Amazon**     | 6            | 7            | A                   |
| **BigBasket**  | 6            | 8            | B                   |
| **Brazilian**  | 8            | 9            | B                   |
| **Customer**   | 8            | 12           | A                   |
| **E-commerce** | 6            | 10           | B                   |


If we focus on pitfalls related to modeling, the most frequent one is *P8. Missing annotations*, which happens for all the ontologies except for the human one for the airlines dataset. *P10. Missing disjointness* and *P13. Inverse relations not explicitly declared* are present in all the LLM ontologies. *P31. Defining wrong equivalent classes* is present in 5 LLM ontologies. If we consider those pitfalls with at least two ocurrences in the human or LLM ontologies, only *P11. Missing domain or range properties* is more frequent in the human ontologies (4 vs 1). *P2. Creating synonyms as classes*, *P34. untyped class*, and *P35. untyped properties* are not exhibited by human ontologies but by most LLM ontologies. These findings suggest that the LLM is modeling in a consistent way across datasets. If we analyse the results by ontologist, the difference in the mean of pitfalls is 4.66 (ontologist A vs LLM) and 2.33 (ontologist B vs LLM).


## Results of the Qualitative Evaluation

### BigBasketProducts

* **Annotations:** The LLM ontology contains more annotations than the human one, including labels in multiple languages, descriptions and comments.

* **Classes:** The LLM ontology has more classes. The LLM includes many equivalentClass axioms, which do not seem correct in some cases. For example "Has offer" is proposed as a class and as an object property with the same URI. The axioms in the human-generated ontology make more sense.

* **Object Properties:** The LLM-generated ontology presents more object properties, but some should not be modelled as  object properties, such as category or subcategory, which should be classes and other properties could have been created. In terms of axiomatic complexity in object properties, both ontologies are similar, with better axioms for inverse object properties, domains and ranges in the human ontologies.

* **Data Properties:** The LLM proposes more datatype properties and creates subhierarchies. The LLM proposes equivalencies between datatype properties, which are sometimes wrong (discounted price and price specification). Both are able to reuse properties from external ontologies, like schema.org. 


 Both ontologies present a similar coverage of the CSV data, but the human-generated ontology presents oportunities for a more detailed modelling.

### BrazilianEcommerce

* **Annotations:** The LLM ontology contains more annotations than the human one, including labels in multiple languages, descriptions and comments.

* **Classes:** The human ontology has more classes. The LLM includes many equivalentClass axioms, which do not seem correct in some cases, for example customer is not equivalent to Person. The LLM misses classes such as seller.

* **Object Properties:** The human ontology present the more object properties, but the domain/range axioms of the LLM are more precise.

* **Data Properties:** The human ontology present more datatype properties, underrepresenting the content of the CSV.

### eCommerce

* **Annotations:**  The LLM ontology contains more annotations than the human one, including labels in multiple languages, descriptions and comments.

* **Classes:** The number of classes are similar. The LLM ontology tend to create equivalent classes to schema classes, but those are not always right (such as consumer and customer) ontologies have exactly the same classes. The human ontology includes more complex and complete axioms in the restricions. The LLM does not generate the individuals generated by the human.

* **Object Properties:** Both ontologies present similar object properties.

* **Data Properties:** The human generated ontology presents more data properties, related to the modelling presented in the classes hierarchy.

### AirlinesCustomerSatisfaction

* **Annotations:** The LLM ontology contains more annotations than the human one, including labels in multiple languages, descriptions and comments.

* **Classes:** The human-generated ontology models some of the entities as individuals rather than classes, and it includes more entities, with a finer modelling, in doing so.

* **Object Properties:** Both ontologies present the same object properties, with identical domain/range. The LLM includes disjointess axioms.

* **Data Properties:** Both ontologies present similar data properties, with identical domain/range.

### AmazonRatings

* **Annotations:** The LLM ontology contains more annotations than the human one, including labels in multiple languages, descriptions and comments.

* **Classes:** Both ontologies have the same number of relevant classes  and the same class names, indicating a similar high-level conceptualization of the domain. However, the LLM adds some other classes, named ErrorX, which are an artifact of the process.

* **Object Properties:** Both ontologies define the same object properties (hasProduct and hasCustomer), suggesting a similar approach to modeling relationships between entities.

* **Data Properties:** This is a significant difference between the two ontologies. The LLM-generated ontology includes data properties that are unnecessary and redundant, like ProductId. Additionally, the DataType ranges are correctly assigned by the human (xsd:string, xsd:double and xsd:int) but the LLM only assignes xsd:string ranges

### CustomerComplaints

* **Annotations:** The LLM ontology contains more annotations than the human one, including labels in multiple languages, descriptions and comments. In some cases, the LLM does not provide annotatins.

* **Classes:** Both ontologies present the same useful classes, but the human-generated ontology presents further subsumption relationships between them. The LLM generates additional classes for establishing equivalencies, without practical usefulness.

* **Object Properties:** Both ontologies present similar object properties, but the human-generated ontology presents more domain/range axioms.

* **Data Properties:** Both ontologies present similar data properties, but the human-generated ontology presents more domain/range axioms.

In general terms, human generated ontologies include:

* Axioms of higher expressivity in class restrictions and properties.
* More accurate linking with entities of external ontologies (e.g. schema), being more interoperable.
* A more nuanced understanding of OWL modelling: instances vs classes, when to add a subsumption relationship, the need for N-ary relationships, etc.

Additionally, some of the LLM-generated ontologies include hallucinations such as entities modeled as both data and object properties, and inappropriate equivalent relations. Finally, the LLM ontologies are consistently richer in annotations, which constitutes an example of how automation could ensure some characteristics of the ontologies generated. Most equivalencies defined between classes in LLM ontologies are inaccurate, and they usually involved entities reused from schema.org. BigBasket Products and Brazilian e-commerce are examples of LLM ontologies with such shortcoming. Regarding the modeling style, Airlines Customer Satisfaction is a significant example. The human modeled the set of satisfaction items as individuals whereas the LLM produced a taxonomy, exhibiting a deeply different modeling style. The LLM exhibits a similar behavior for the CustomerComplaint datasets. For both datasets, the number of object and datatype properties of the human and LLM ontologies are quite similar, the most significant difference happening for the number of classes. 

The LLM ontologies are richer in annotations.


## Results of the Estimation of time saving

The next table shows the results of the estimation of the time saved for each dataset. The column "Human modeling" stands for the time spent by the human in creating the ontology from scratch. The column LLM Review includes both the time in generating the OntoGenix ontology and the time spent by the human in reviewing that ontology. The column LLM2Human is the time spent by the human in creating the human ontology from the OntoGenix one. The column Time saved is the difference between Human Modeling and the sum LLMReview + LLM2Human. The column Percentage stands for the percentage of time saved, and the column Effort represents the qualitative assessment of the effort for transforming the OntoGenix ontology in the human one.

The generation of the OntoGenix ontology has reduced the total time for generating the human ontology in all the cases, with savings (in minutes) ranging from 26.2 to 218.6 in absolute terms, and from 8.2% to 58.3% in percentage.Regarding the assessment of the effort needed for transforming the OntoGenix ontology into the human one, in all the cases the effort was evaluated 3 (moderate effort) or lower, the most frequent being low effort. 

| **Time (min)**     | **Human Modelling** | **LLM Review** | **LLM2Human** | **Time saved** | **Percentage** | **Effort (1-5)** |
|----------------|---------------------|----------------|---------------|----------------|----------------|------------------|
| **Airlines**   | 369,0               | 192,6          | 22,0          | -154,4         | -41,8          | 2                |
| **Amazon**     | 108,8               | 51,0           | 5,0           | -52,8          | -48,5          | 1                |
| **BigBasket**  | 236,3               | 139,2          | 27,0          | -70,1          | -29,7          | 2                |
| **Brazilian**  | 105,0               | 58,2           | 12,0          | -34,8          | -33,1          | 2                |
| **Customer**   | 318,0               | 262,8          | 29,0          | -26,2          | -8,2           | 3                |
| **E-commerce** | 375,0               | 104,4          | 52,0          | -218,6         | -58,3          | 3                |

### Summary of the findings

The assessment of the ontologies generated by the LLM shows that they are not as adequate as the human-developed ones, which are more comprehensive and aligned with the content and structure of the CSV files. The qualitative evaluation of the ontologies reveal that despite LLM ontologies being richer in annotations and in many cases producing a similar number of classes and properties, they are still behind the human reasoning for modeling complex contexts. These findings are also supported by the results of the quantitative metrics, which show differences in metrics related to annotation properties in favor of the LLM, but the human ones have higher scores for metrics related to the taxonomy or the number of paths, which deal with the complexity of the structure of the ontology. The scores of some metrics related to the number and usage of properties are also higher for the LLM ontologies, but we do not draw any strong conclusion due to the suboptimality of some design decisions when qualitatively inspected. The analysis of the pitfalls is similar, suggesting that the LLM is modeling in a consistent way, with identified strengths and aspect to improve. 
