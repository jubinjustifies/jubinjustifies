

<h1 align="center">Hi, I'm Jubin Sharma 👋</h1>
<h3 align="center">Senior Data Engineer with 7+ years experience across Tech & Banking domain</h3>

<p align="center"> 
  <a href="https://linkedin.com/in/sharmajubin" target="_blank">
    <img src="https://img.shields.io/badge/-Jubin%20Sharma-blue?style=for-the-badge&logo=Linkedin&logoColor=white" alt="LinkedIn"/>
  </a> 
  <a href="https://rosh-portfolio.vercel.app/" target="_blank">
    <img src="https://img.shields.io/badge/-My%20Portfolio-purple?style=for-the-badge&logo=About.rp&logoColor=white" alt="Portfolio" />
  </a>
</p>


<p align="center"> 
  🚀 Visitor count<br>
  <img src="https://komarev.com/ghpvc/?username=jubinjustifies&color=brightgreen&style=for-the-badge" alt="Profile Views"/>
</p>


## 💫 About:

* 💡 With 7+ years of professional experience in designing pipelines on Big Data frameworks for Banking Industry.
* 🚀 Passionate about exploring and learning new skills.
* 🤝 Technology enthusiast & a team player.
* 🎤 Good communication and presentation skills.
* 🎓 Completed Diploma PG in Big Data Analytics from CDAC ACTS, Pune.
* ⚙️ Comfortable in developing ETL pipelines using Hadoop, Spark, Hive, Kafka, NiFi, Beam, Oozie, Kubernetes.
* ☁️ Hands-on experience in GCP services such as Dataflow, KMS, GKE, Pub/Sub, Storage, Spanner, BigQuery, and IAM.
* 👨‍💻 Have good programming experience with Core Java, Scala, and Python.
* 📊 Implemented multiple ETL processes to streamline the import of data into Big Query warehouse and transforming them as per the downstream consumer requirements.
* 🏗️ Experienced in designing and developing data integration solutions using AWS based tools such as DMS, Step Functions, EventBridge, Cloud Functions, EMR, SQS, SNS, Cloudwatch.
* 🛠️ Implemented pipeline to create GCP resources using automated infrastructure provisioning through Terraform scripts.
* 🔄 Designed & managed CI/CD pipeline using Jenkins, Harbor, Spinnaker for multiple Route to Live Environments.

---
## 🏗️ Projects:

### 🏆 Metadata Enrichment Framework (Data Cataloging service within GCP)

- Developing an automated system to ingest the Business and Technical Metadata using the Dataplex Catalog REST APIs.
- The design includes flask-based routes that creates/updates the Aspects to the GCP Assets intelligently based on a certain provided aspect type.
- Another restricted route helps the Governance users to create/update Aspect Type based on user provided content or fetching the information from the client's older Cataloging tool, Collibra.
- The configuration of this Aspect Manager service is placed in Big Query table which needs to be updated using another route created specifically for overwriting this table entry.
- The framework is used to onboard different data product teams on Dataplex Catalog and the configurations needs to be updated by the owner of the team.
- At the moment the service supports adding Aspects to Spanner and Big Query system entries, working on the GCS entries.
- Challenges were encountered while using RPC to control Dataplex since we cannot add Aspects to System Entries. This operation can only be performed using the REST call which happens in the console as well.

### 🔍 Consumer Risk Data Product (GCP based ETL)

- Consumer Risk Data ingested from Relational data Hub(On Premises) to System Of Insights (GCP layer).
- JSON events from Spanner are published into Raw layer(BQ) using a GKE cronjob triggered batch-based Dataflow pipeline further reconciling and publishing the status in the metadata tables.
- Pub/Sub event driven microservices flattens the data into Staging layer(BQ) and transforms into Curation layer(BQ) populating the SOI.

### 🔧 Infrastructure Provisioning Automation (Terraform based GCP resource provisioning module)

- Automating the infrastructure provisioning for Risk Domain by introducing Terraform based GCP resource creation with domain and team specific access controls.
- Created domain specific repository to hold the configurations that were baked on the terraform script deploying the resources in multiple environments with proper guardrails and naming conventions.

### 🚀 CICD Pipeline (GKE based Jenkins pipeline)

- Designing the CI & CD Jenkins job to source, build, deploy & release the cronjob, dataflow pipeline and staging & curation microservices in various environments on Google Kubernetes Engine using Helm.

### 💰 Commercial Risk Data Product (GCP based ETL)

- Commercial Risk Data migrated from Enterprise data Hub(On Premises) to System Of Engagement (GCP layer) using a GKE based batch processing pipeline.
- Cron triggered Cloud Dataflow ingests the JSON data from Landing layer(Spanner) into the Raw layer(BQ) further running a Reconciliation job updating a metadata tables and publishing the events into the topic(Pub/Sub) triggering the listener microservice, flattening & transforming the data into Staging(BQ) and Curation(BQ) layers for downstream consumption from SOE layer.

### ⚡ CICD Pipeline (AWS based service)

- Designing AWS CodePipeline using Cloudformation Stacks/CFT in YAML.
- This includes automated deployment of code using Code Source, Code Build and Code Deploy.
- All the AWS resources like Lambda, State Machine, Bucket, Policies & Roles are defined within the CFT and deployed using the CodePipeline which is also deployed by a CICD CFT.

### 🔄 E2E AWS Data Pipeline

- Designing an E2E data pipeline using AWS for Banking domain data.
- The pipeline contains Ingestion service that ingress data from Kafka topic within an On-premises cluster using Spark-Scala developed code.
- The ingestion also happens from various replications tasks defined for Full load and CDC using Database Migration Service where the source is Oracle.
- Since the data has PCI and PII columns, Data anonymization service(Spark-Scala) is developed to do SHA-256 encryption on the S3 data that is ingested.
- Later the Transformation service joins and unions the data using Spark Scala code.
- The spark-submit is done using lambda functions which send Livy submit to the EMR.
- Every stored location can be queried using Athena since Glue crawlers are enabled on top of it.
- The whole project is scheduled using Cloudwatch Rules and are orchestrated using Step function state machines.
- All the resources like EMR, Lambda, Step function, S3, Cloudwatch, IAM Roles, etc. are created by Cloudformation.
- The deployment of all the resources in various environments like Dev, QA, Prep, Prod are also automated using Code pipeline with just a Cloudformation stack.

### 🌍 Public Dataset Analysis (Service on GCP)

- Public Datasets including data on Census, Election, Geography, Crime and Economics available on various govt. sites are ingested by web scraping and api calls.
- Data granularity is checked, and they are merged together to form a master dataset of pincode level granularity.
- This master dataset can be merged by any dataset to get analysis on various factors.
- Python code running on cloud functions does the merge and data processing, the data was stored on cloud storage.

### 🔥 Batch & Stream data processing GCP-based pipeline

- The project utilizes Google cloud platform to build a batch and stream data processing pipeline.
- The stream data source provides an endpoint with which response JSON data can be ingested into the pipeline with a certain Cloud schedule that triggers the Cloud functions. The JSON is published into a Cloud PubSub Topic using python on Cloud functions.
- Later it is subscribed and dumped as-is in Cloud storage.
- The batch data is also ingested from SFTP server via running spark jobs on Compute engine with a prebuilt VM image of the environment having required dependencies fulfilled.
- Once the data for both batch and stream data are ingested in the storage, a scheduled job picks it up and parses into the desired data format using DataFlow.
- The output of dataflow is again GCS but is partitioned with the eventdate and eventhour.
- Data Analysts can now easily query this data from BigQuery.
- The output of BigQuery is also visualized in desired graphs using Data Studio.

### ☁️ Azure-based Data processing pipeline

- The project involves building Data ingestion RESTful API service which keeps running eternally.
- A call to this service loads a Nifi predefined data load template which validates the schema as per the Schema Registry and reads data from a landing location on Azure Data Lake Storage and writes it in an ADLS raw data location.
- Hive partitioned tables are also created on top of this raw layer.
- Now the downstream process, Data transformation service that picks data from this raw location is triggered via Oozie scheduler.
- The transformation service is an implementation of Type 2 SCD which is developed in Spark-Scala.
- The spark submit command reads data from the ADLS and according to its intelligence identifies the insert and update records in a transaction and writes the latest record in the curated layer with Hive enabled on it.
- Service can also utilize I,U,D flags to determine the latest record after performing the inserts, updates and deletes.
- The roles and governance were managed by Atlas.
- Data visualizations were handled by PowerBI.

### 🏴‍☠️ Bitcoin Blockchain Data Analyzer

- The project includes preparing and preprocessing of blockchain json block data.
- The json data is ingested in Hadoop Distributed File System with Object Relationship Mapping through Plain Old Java Objects with Jackson library and Encoders.
- The HDFS block data is fetched by the algorithm to find the block elements that contain specific buyers that are into the fradulent money trail.
- Later the gathered data by Spark or SparkSQL can be dumped into MongoDB through which it can be easily used by Tableau to do some data visualization.
---

## Certifications:

- [**List**](https://www.linkedin.com/in/sharmajubin/details/certifications/)  

---
## 💻 Tech Stack:

### 🛠️ Languages & Tools:
![SQL](https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
![Scala](https://img.shields.io/badge/Scala-DC322F?style=for-the-badge&logo=scala&logoColor=white)
![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)

### 🗄️ Databases:
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![MS SQL](https://img.shields.io/badge/MS_SQL_Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

### 📊 BI Tools:
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)
![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

### ⚙️ Data Engineering Tools:
![Apache Spark](https://img.shields.io/badge/Apache_Spark-E25A1C?style=for-the-badge&logo=apache-spark&logoColor=white)
![Apache Hadoop](https://img.shields.io/badge/Apache_Hadoop-66CCFF?style=for-the-badge&logo=apache-hadoop&logoColor=black)
![Apache Hive](https://img.shields.io/badge/Apache_Hive-FDEE21?style=for-the-badge&logo=apache-hive&logoColor=black)
![Apache NiFi](https://img.shields.io/badge/Apache_NiFi-005571?style=for-the-badge&logo=apache-nifi&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white)
![Apache Airflow](https://img.shields.io/badge/Airflow-017CEE?style=for-the-badge&logo=apache-airflow&logoColor=white)
![Apache Sqoop](https://img.shields.io/badge/Apache_Sqoop-8A3FFC?style=for-the-badge&logo=apache-sqoop&logoColor=white)

### ☁️ Cloud & CI/CD:
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-0db7ed?style=for-the-badge&logo=docker&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)
![Spinnaker](https://img.shields.io/badge/Spinnaker-139BB4?style=for-the-badge&logo=spinnaker&logoColor=white)

