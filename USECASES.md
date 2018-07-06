
## 1. Other business scenarios that this approach can help build a solution 

There are two methods of correlating text content that have been described in this code pattern. 

- **Extraction of entities and relations in the text content across documents**

A text can contain entities and relations. For example the text can talk about - people, locations, etc and the relationships between them. In such cases, the entities and relations are extracted from text content across all the documents. A graph is built using all the extracted entities and relations. When entities repeat between documents, the text content is automatically correlated across documents. 

In this pattern, the Watson Natural Language output is augmented with the rules based approach described. There can be requirements where we are interested in extracting specific *known* relations in our text content. An example - Extract all `educatedAt` relations in the documents. In addition, there could be no documents available for training. In such cases, using a rules based approach of extracting relations between entities could be preferred and is demonstrated in this code pattern.

- **Text similarity between text content across documents**

There are known entities that could have a text description associated with them. There can be a need to correlate the entities based on the similarity of the text desacription. Take the example of software development artifacts. We might want to correlate a `defect` to a `requirement`. The similarity of the `defect` description and `requirement` description can be used to correlate the two artifacts or entities.

> Note: The code and configuration provided in this repository can be modified to build a solution for the above scenarios. 

## 2. Other Usecases that this approach can help build a solution

### (I) Correlate software development artifacts
 
In the software development lifecycle, there are many artifacts that are generated - requirements, testcases, defects etc. In long running software projects with minimal tool support and a churn of team members, the new team members face many questions:

    What requirement does this defect correlate to?
    What are the testcases that I need to execute after a defect is fixed? and so on.

Please refer to the composite code pattern that uses this code pattern to achieve correlation between software development artifacts - [Mine insights from software development artifacts](https://developer.ibm.com/code/patterns/mine-insights-from-software-development-artifacts/) for the methodology.

### (II) Order Reconciliation and Dispute Resolution  

A supplier wants to reconcile order items, quantity and price across various documents such as purchase orders, bills, delivery notes, mails etc. This could be for an audit or for dispute redressal. The text similarity approach described in the pattern can be used to correlare purchase orders, bills, delivery notes and other artifacts.
Please refer the blog [Correlate personal finance information](https://developer.ibm.com/code/?p=29292&preview=true) to see the approach.

### (III) Product recommendations

An online retailer can recommend products to prospective customers based on the browsing history and previous purchases. Every product has a description and specifications. The similarity between products can be found by comparing their description and specifications. The text similarity feature described in this pattern can be used to correlate products. The products that correlate the most with what the prospective customer is viewing or purchased have better chance of resulting in a sale. Such products can be recommended to the customer.

### (IV) Investment recommendation

Every investor looks out for recommendations to buy or sell a stock based on how it is expected to perform. The information about a company is available on news portals, company web sites, stock exchange portals or other sources. A company performance is affected by deals, mergers and other actions. If such information is extracted from the data sources and presented to the prospective investor as and when the information appears, the investor is well informed with the latest information to make a decision with regard to a company stock. This pattern can help extract such information in the form of relations. For example - Company ABC signed a deal with Company XYZ. This can be extracted as a relation - (ABC, dealSign, XYZ). A knowledge graph about a company stock can be built with all these relations and presented to the investor enabling decision making. 
