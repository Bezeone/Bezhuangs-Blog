---
title: Tools for Data Science
date: 2021-04-19
updated: 2021-05-02
tags: []
categories: 人工智能与大数据
---

> In this course provided by IBM, I learned about Jupyter Notebooks, JupyterLab, RStudio IDE, Git, GitHub, and Watson Studio, what each tool is used for, what programming languages they can execute, their features and limitations. With the tools hosted in the cloud on Skills Network Labs, I can now run simple code in Python, R or Scala. The following are the notes I took during this course.

<!--more-->

{% pdf /pdf/Tools-for-Data-Science.pdf %}

### Languages of Data Science

- Python
  - General Purpose language with Large standard library
  - Scientific computing libraries like Pandas, NumPy, SciPy and Matplotlib
  - For artificial intelligence it has PyTorch, TensorFlow, Keras and Scikit-learn
  - Python can be used for Natural Language Processing (NLP) using the Natural Language Toolkit (NLTK)
- R Language
  - Python is Open Source, R is Free Software
  - Open Source Initiative (OSI) champions open source while the Free Software Foundation (FSF) defines free software
  - Open Source is more business focused while Free Software is more focused on a set of values
  - R is most often used by statisticians, mathematicians and data miners for developing statistical software, graphing and data analysis
  - The array-oriented syntax makes it easier to translate from math to code
  - R has become the world's largest repository of statistical knowledge
  - Common mathematical operations like matrix multiplication work straight out of the box
  - R has stronger object-oriented programming facilities than most statistical computing languages 
- SQL (Structured Query Language)
  - SQL = 
  - SQL was initially developed at IBM, first appeared in 1974
  - Useful in handling structured data, i.e. data incorporating relations among entities and variables
  - The SQL language is subdivided into several language elements, including clauses, expressions, predicates, queries, and statements
  - Knowing SQL will help you do many different jobs in data science, including business and data analyst, and it's a must in data engineering. 
  - When performing operations with SQL, you access the data directly ( without any need to copy it beforehand). This can speed up workflow executions considerably.
  - SQL is the interpreter between you and the database
  - SQL is an American National Standards Institute, or "ANSI," standard, which means if you learn SQL and use it with one database, you will be able to easily apply that SQL knowledge to many other databases.
  - MySQL, IBM Db2, PostgreSQL, Apache OpenOffice Base, SQLite, Oracle, MariaDB, Microsoft SQL Server
- Java
  - Java is a tried and true general purpose object oriented programming language
  - Huge adoption in the enterprise space, designed to be fast and scalable
  - Java applications are compiled to bytecode and run on JVM
  - Tools include Weka (data mining), Java-ML (ml library), Apache MLlib (scalable ml) and Deeplearning4j
  - Hadoop manages data processing and storage for big data applications running in clustered systems
- Scala
  - Scala is a general purpose programming language that provides support for functional programming
  - Designed as an extension to Java, it is inter-operable with Java as it also runs on JVM
  - The name Scala comes from "Scalable Language"
  - Apache Spark is a fast and general-purpose cluster computing system. It provides APIs that make parallel jobs easy to write, and an optimized engine that supports general computation graphs.
  - Spark includes Shark, which is a query engine; MLlib, for machine learning; GraphX, for graph processing; and Spark Streaming. 
  - Apache Spark was designed to be faster than Hadoop
- C++
  - Another general purpose language, C++ is an extension of C
  - Improve processing speed, enables system programming and gives you broader control over the application
  - Many organizations rely on C++ to develop programs that feed data to customers in real-time
  - TensorFlow is a deep learning library
  - MongoDB is a NoSQL database for big data management
  - Caffe is a deep learning algorithm repository
- Javascript
  - A core technology for the WWW, A general purpose language that extended beyond the browser with Node.js and other server side approaches
  - TensorFlow.js makes machine learning and deep learning possible in Node.js and in the browser, It is adopted by other open source libraries including brain.js and machinelearn.js
  - R-js makes linear algebra possible in Typescript
- Julia
  - Designed at MIT for high-performance numerical analysis and computational science
  - Same speedy development like Python or R while producing programs that run as fast as C or Fortran programs would
  - It's compiled, calls C, Go, Java, MATLAB, R, Fortran and Python libraries and has refined parallelism
  - A young language with a lot of promise in the data science industry
  - JuliaDB is a particularly useful application of Julia for data science. It's a package for working with large persistent data sets.

### Data Science Tools

- Data Management tools: persisting and retrieving data
  - Open Source: MySQL, PostgreSQL, MongoDB, Apache CouchDB, Apache Cassandra, Hadoop File System, Ceph(Cloud File systems), Elasticsearch
  - Commercial: Oracle Database, Microsoft SQL Server, IBM Db2
  - SaaS(cloud based): Amazon DynamoDB, Cloudant(based on CouchDB), Db2
- Data Integration and Transformation tools: ETL(extract, transform, load)
  - Open Source: Apache AirFlow, KubeFlow, Apache Kafka, Apache Nifi, Apache SparkSQL, NodeRED
  - Commercial: Informatica, IBM InfoSphere DataStage, Talend
  - Cloud Based(ELT): Informatica, IBM Data Refinery
- Data Visualization tools
  - Open Source: Hue, Kibana, Apache Superset
  - Commercial: Tableau, Microsoft Power BI, IBM Cognos Analytics
  - Cloud Based: Datameer, IBM Cognos Analytics
- Model Building: creating a machine learning or deep learning model using an appropriate algorithm
  - Commercial: SPSS Modeler, SAS Enterprise Miner
  - Cloud Based: IBM Watson Machine Learning, Google Cloud
- Model Deployment tools: make machine learning or deep learning model consumable
  - Open Source: Apache PredictionIO, Seldon, Mleap, TensorFlow Service, TensorFlow lite
  - Commercial: SPSS Collaboration and Deployment Service
- Model Monitoring and Assessment tools: keep track of prediction performance
  - Open Source: ModelDB, Prometheus, IBM AI Fairness 360 open source toolkit, IBM Adversarial Robustness 360 Toolbox, IBM AI Explainability 360 Toolkit
  - Cloud Based: Amazon SageMaker Model Monitor, Watson OpenScale
- Code Asset Management tools: versioning and other collaborative features to facilitate teamwork
  - Open Source: git, Github, GitLab, Bitbucket
- Data Asset Management tools: supports replication, backup, and access right management
  - Open Source: Apache Atlas, ODPi Egeria, Kylo
  - Commercial: Informatica, IBM InfoSphere Information Governance
- Development Environments (IDE): help data scientistd to implement, execute, test and deploy their work
  - Open Source: Jupyter notebook, Jupyter lab, Apache Zeppelin, R Studio, Spyder
- Execution Environments: where data processing, model training and deployment take place
  - Open Source: Apache Spark, Apache Flink, Ray
- Fully Integrated Visual Tools
  - Open Source: KNIME, Orange
  - Cloud Based: Watson Studio, Open Scale, Azure Machine Learning, H2O Driverless AI

### Packages, APIs, Data Sets and Models

- Libraries for Data Science
  - Scientifics Computing Libraries: Pandas, NumPy
  - Visualization Libraries: Matplotlib, Seaborn
  - Machine Learning and Deep Learning: Scikit-learn, Keras
  - Deep Learning Libraries: TensorFlow, PyTorch
  - Apache Spark
  - Scala-Libraries: Vegas(statistical data visualization), BigDL
  - R-Libraries: Ggplot2
- Application Programming Interfaces (API)
  - REST APIs (Representational, State, Transfer): used to interact with web services
  - REST APIs have a set of rules regarding communication, input or request, output or response
- Data Sets
  - A data set is a structured collection of data
  - Tabular data: CSV (comma separated values)
  - Hierarchical data, Network data
  - Raw files: images and audio
- Data Ownership
  - Private data: Confidential, Private or personal information, Commercially sensitive
  - Open data: Scientific institutions, Governments, Organizations, Companies, Publicly available
  - Kaggle, datacatalogs.org, Google data set search
  - CDLA: Community Data License Agreement

- Data Asset eXchange
  - Curated collection of data sets
  - Data Science friendly licences
- Machine Learning Models
  - 