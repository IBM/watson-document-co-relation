# Correlation of text content across documents using Watson Natural Language Understanding, Python NLTK and IBM Data Science experience

In this developer journey we will use Jupyter notebooks in IBM Data Science experience(DSX) to correlate text content across documents with Python NLTK toolkit and IBM Watson Natural Language Understanding. The correlation algorithm is driven by an input configuration json that contains the rules and grammar for building the relations. The configuration json document can be modified to obtain better correlation results between text content across documents.

When the reader has completed this journey, they will understand how to:

* Create and run a Jupyter notebook in DSX.
* Use DSX Object Storage to access data and configuration files.
* Use IBM Watson Natural Language Understanding API to extract metadata from documents in Jupyter notebooks.
* Extract and format unstructured data using simplified Python functions.
* Use a configuration file to specify the co-reference and relations grammar.
* Store the processed output JSON in DSX Object Storage.

The intended audience for this journey is developers who want to learn a method for correlation of text content across documents. The distinguishing factor of this journey is that it allows a configurable mechanism of text correlation. 

![](doc/source/images/architecture.png)

## Included components

* [IBM Data Science Experience](https://www.ibm.com/bs-en/marketplace/data-science-experience): Analyze data using RStudio, Jupyter, and Python in a configured, collaborative environment that includes IBM value-adds, such as managed Spark.

* [Bluemix Object Storage](https://console.ng.bluemix.net/catalog/services/object-storage/?cm_sp=dw-bluemix-_-code-_-devcenter): A Bluemix service that provides an unstructured cloud data store to build and deliver cost effective apps and services with high reliability and fast speed to market.

* [Watson Natural Language Understanding](https://console.bluemix.net/catalog/services/natural-language-understanding/?cm_sp=dw-bluemix-_-code-_-devcenter): A Bluemix service that can analyze text to extract meta-data from content such as concepts, entities, keywords, categories, sentiment, emotion, relations, semantic roles, using natural language understanding.

## Featured technologies

* [Jupyter Notebooks](http://jupyter.org/): An open-source web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text.


# Watch the Video

[![](http://img.youtube.com/vi/vDCaBPhAr64/0.jpg)](https://youtu.be/vDCaBPhAr64)

# Steps

Follow these steps to setup and run this developer journey. The steps are
described in detail below.

1. [Sign up for the Data Science Experience](#1-sign-up-for-the-data-science-experience)
1. [Create Bluemix services](#2-create-bluemix-services)
1. [Create the notebook](#3-create-the-notebook)
1. [Add the data and configuraton file](#4-add-the-data-and-configuration-file)
1. [Update the notebook with service credentials](#5-update-the-notebook-with-service-credentials)
1. [Run the notebook](#6-run-the-notebook)
1. [Analyze the results](#7-analyze-the-results)

## 1. Sign up for the Data Science Experience

Sign up for IBM's [Data Science Experience](http://datascience.ibm.com/). By signing up for the Data Science Experience, two services: ``DSX-Spark`` and ``DSX-ObjectStore`` will be created in your Bluemix account.

## 2. Create Bluemix services

Create the following Bluemix service and name it wdc-NLU-service:

  * [**Watson Natural Language Understanding**](https://console.bluemix.net/catalog/services/natural-language-understanding)
  
  ![](doc/source/images/bluemix_service_nlu.png)

## 3. Create the notebook

In [Data Science Experience](http://datascience.ibm.com/):

Use the menu on the top to select `Projects` and then `Default Project`. 
Click on `Add notebooks` (upper right) to create a notebook.

* Select the `From URL` tab.
* Enter a name for the notebook.
* Optionally, enter a description for the notebook.
* Enter this Notebook URL: https://github.com/IBM/watson-document-co-relation/blob/master/notebooks/watson_correlate_documents.ipynb
* Click the `Create Notebook` button.

![](doc/source/images/create_notebook_from_url.png)

## 4. Add the data and configuration file

#### Add the data and configuration to the notebook

* From the `My Projects > Default` page, Use `Find and Add Data` (look for the `10/01` icon)
and its `Files` tab. 
* Click `browse` and navigate to this repo `watson-document-classifier/data/sample_text_1.txt`
* Click `browse` and navigate to this repo `watson-document-classifier/data/sample_text_2.txt`
* Click `browse` and navigate to this repo `watson-document-classifier/configuration/sample_config.txt`

![](doc/source/images/add_file.png)

> Note:  It is possible to use your own data and configuration files.
If you use a configuration file from your computer, make sure to conform to the JSON structure given in `configuration/sample_config.txt`.

#### Fix-up file names for your own data and configuration files

If you use your own data and configuration files, you will need to update the variables that refer to the data and configuration files in the Jupyter Notebook.

In the notebook, update the global variables in the cell following `2.3 Global Variables` section.

Replace the `sampleTextFileName1`,`sampleTextFileName2` with the name of your data file and `sampleConfigFileName` with your configuration file name.

![](doc/source/images/update_variables.png)

## 5. Update the notebook with service credentials

#### Add the Watson Natural Language Understanding credentials to the notebook
Select the cell below `2.1 Add your service credentials from Bluemix for the Watson services` section in the notebook to update the credentials for Watson Natural Langauage Understanding. 

Open the Watson Natural Language Understanding service in your [Bluemix Dashboard](https://console.bluemix.net/dashboard/services) and click on your service, which you should have named `wdc-NLU-service`.

Once the service is open click the `Service Credentials` menu on the left.

![](doc/source/images/service_credentials.png)

In the `Service Credentials` that opens up in the UI, select whichever `Credentials` you would like to use in the notebook from the `KEY NAME` column. Click `View credentials` and copy `username` and `password` key values that appear on the UI in JSON format.

![](doc/source/images/copy_credentials.png)

Update the `username` and `password` key values in the cell below `2.1 Add your service credentials from Bluemix for the Watson services` section.

![](doc/source/images/watson_nlu_credentials.png)

#### Add the Object Storage credentials to the notebook
* Select the cell below `2.2 Add your service credentials for Object Storage` section in the notebook to update the credentials for Object Store. 
* Delete the contents of the cell

* Use `Find and Add Data` (look for the `10/01` icon) and its `Files` tab. You should see the file names uploaded earlier. Make sure your active cell is the empty one below `2.2 Add...`  
* Select `Insert to code` (below your sample_text.txt). 
* Click `Insert Crendentials` from drop down menu.
* Make sure the credentials are saved as `credentials_1`.

![](doc/source/images/objectstorage_credentials.png)

## 6. Run the notebook

When a notebook is executed, what is actually happening is that each code cell in
the notebook is executed, in order, from top to bottom.

> IMPORTANT: The first time you run your notebook, you will need to install the necessary
packages in section 1.1 and then `Restart the kernel`.

Each code cell is selectable and is preceded by a tag in the left margin. The tag
format is `In [x]:`. Depending on the state of the notebook, the `x` can be:

* A blank, this indicates that the cell has never been executed.
* A number, this number represents the relative order this code step was executed.
* A `*`, this indicates that the cell is currently executing.

There are several ways to execute the code cells in your notebook:

* One cell at a time.
  * Select the cell, and then press the `Play` button in the toolbar.
* Batch mode, in sequential order.
  * From the `Cell` menu bar, there are several options available. For example, you
    can `Run All` cells in your notebook, or you can `Run All Below`, that will
    start executing from the first cell under the currently selected cell, and then
    continue executing all cells that follow.
* At a scheduled time.
  * Press the `Schedule` button located in the top right section of your notebook
    panel. Here you can schedule your notebook to be executed once at some future
    time, or repeatedly at your specified interval.

## 7. Analyze the results

After running each cell of the notebook under Correlate text, the results will display. 

The configuration json controls the way the text is correlated. The correlation involves two aspects - co-referencing and relation determination. The configuration json contains the rules and grammar for co-referencing  and determining relations. The output from Watson Natural Language Understanding and Python NLTK toolkit is processed based on the rules and grammar specified in the configuration json to come up with the correlation of content across documents. 

![](doc/source/images/correlate_text_config.png)

We can modify the configuration json to add more rules and grammar for co-referencing and determining the relations. The text content correlation results can be enhanced without changes to the code.

We can see from the `6. Visualize correlated text` in the notebook the correlations between the text in the two sample documents that we provided.

![](doc/source/images/network_graph.png)

# Troubleshooting

[See DEBUGGING.md.](DEBUGGING.md)

# License

[Apache 2.0](LICENSE)
