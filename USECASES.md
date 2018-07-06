
## 1. Other business scenarios that this approach can help build a solution 

There are two methods of correlating text content that have been described in this code pattern. 

- **Extraction of entities and relations in the text content across documents**
A text can contain entities and relations. For example the text can talk about - people, locations, etc and the relationships between them. In such cases, the entities and relations are extracted from text content across all the documents. A graph is built using all the extracted entities and relations. When entities repeat between documents, the text content is automatically correlated across documents. 

In this pattern, the Watson Natural Language output is augmented with the rules based approach described. There are requirements where we are interested in extracting specific relations in our text content and they are known. In addition, there could be no documents available for training. In such cases, using a rules based approach of extracting relations between entities is preferred and is demonstrated in this code pattern.

- **Text similarity between text content across documents**
There are known entities that could have a text description associated with them. There can be a need to correlate the entities based on the similarity of the text desacription. Take the example of software development artifacts. We might want to correlate a `defect` to a `requirement`. The similarity of the `defect` description and `requirement` description can be used to correlate the two artifacts or entities.

> Note: The code and configuration provided in this repository can be modified to build a solution for the above scenarios. 

## 2. Other Usecases that this approach can help build a solution
