# SAP HANA
This will majorly focus on the steps of implementing SAP HANA Environment to fulfill the organization’s BI needs. To analyze huge amount of data, SAP HANA is a perfect solution as it is based on in-memory database. The first step is to create a data model based on source data, and then populate it with the relevant data which will be further analyzed and visualized.

## About SAP HANA

SAP HANA is a high-performance in-memory database that provides advanced analytics on multi-model data, on premise and in cloud. As the data is stored in its memory, the data processing is very fast as compared to disk-based data systems allowing advanced and real-time analytics. It is used for transactional and analytical workloads with any kinds of data. It serves as a platform for enterprise resource planning (ERP) software and other business applications. SAP HANA can be placed on premises, in the cloud or both in a hybrid cloud system and is therefore used in multiple areas within an organization. I chose this tool for my portfolio to learn more about the implementation of SAP HANA Environment and understanding how it enhances customer satisfaction by providing so many features such as predictive analytics, integrating team workflows, and many more. Following are the key capabilities of this tool (IBM, 2022):

 - SAP HANA’s in-memory, multi-model data management capabilities minimize the data movements, thus increasing the application speed and agility to efficiently analyze real-time data.
 - It can be deployed on premises, in the cloud or as a hybrid system based on the user needs.
 - It is very efficient in processing enormous amounts of data to make it a suitable option for enterprises without sacrificing security or stability.
 - SAP HANA’s machine learning engine extracts data from and writes to the server in real-time, which helps in identifying problems and their solutions instantly.

## Implementation of SAP HANA Environment

In this section, the major focus is on the steps of implementing SAP HANA Environment to fulfill the organization’s BI needs. To analyze huge amount of data, SAP HANA is a perfect solution as it is based on in-memory database. The first step is to create a data model based on source data, and then populate it with the relevant data.

##### Step 1: Create Sales Transaction, Customer Master, and Product Master database tables

In SAP HANA Catalog, under the package GBI-student-429 each table will be created by adding a new file named as CUSTOMER_ATTR_429.hdbtable, PRODUCT_ATTR_429.hdbtable, and SALES_429.hdbtable. All these tables will be created in the schema GBI_429. A schema is the organization of data as a blueprint of how the database is constructed. Following figures show Customer Attribute Database Table, Product Attribute Database Table, and Sales Attribute Database Table respectively.

##### Step 2: Data Provisioning

This step includes populating the database tables using Smart Data Integration Tool. It allows to securely transfer critical business data to and from the SAP HANA database, enabling the user to easily synchronize and share the data within an organization (Muthaiah, 2021). To do this, a data flow is created that extracts data from a flat file to further transfer it into database tables respectively. The first step is to add a new remote source to the SAP HANA system in Provisioning. It defines an external data source connected to the system, and only the database users having the system privilege are allowed to do so. When this is done, the user can view the CSV files of Customer, Product, and Sales data.

Then a Virtual Data Table is created using the remote source, which points to remote files. It allows the user to access objects in remote sources without having to replicate it to the SAP HANA database (SAP, 2022).

After this, in Editor perspective of SAP HANA Web Workbench, a new flowgraph model is created to load the data for each table i.e., Customer Flow, Product Flow, and Sales Flow. Here, a data connection is established between virtual table (data source) and data table (data sink) as shown in the following figures: Customer Flow, Product Flow, and Sales Flow respectively. Once all the models are executed, the content can be seen in the data tables in the Catalog perspective.

##### Step 3: Create Calculation View for Customer Data, Product Data, and Sales Data

A Calculation View is a flexible information view that can be used to define more advanced slices on the data available in the SAP HANA database (SAP, 2022). It can mirror the functionalities found both in attribute and analytic views. In this case, tables do not contain the textual descriptions of few fields, which are kept in separate text tables. Therefore, this data needs to be merged using the text join on customer attributes table and text tables for country and sales organization. Also, any filters can be applied here as per the requirements, in this case only the data valid to date 9999-12-31 is considered. Then, all the necessary fields are mapped from source to output columns in the mapping tab of a new projection. After creating the projection nodes and linking it to the respective join nodes, following will be the outputs shown in Figures: Customer Calculation View, Product Calculation View, and Sales Calculation View respectively.

In case of Sales, a star join is created, and the projection node in linked with star join node as shown in the following figure. Sales table is joined with customer view using the field customer number and a referential join whereas, it is joined with product view using the field product and referential join.

##### Step 4: Analyze Sales Data using SAP Predictive Analytics

Sales Calculation View is imported from SAP HANA into the Expert Analytics and further analysis is performed.

## Dataset and Research questions

The Sales dataset is imported to perform the analysis which also contains the data from both customer table and product table. It contains many fields related to product, customer, sales organization, sales quantity, net revenue, and many more as shown in the Figure 46. To answer the following research questions, the main point of focus will be on the net revenue generated by each sales organization. Net Revenue is a calculated field created in Step 3 of implementing SAP HANA Environment using: Revenue – Discount.

 - Which Sales Organization has highest and lowest net revenue?
 - What is the trend observed for each of the sales organization in terms of their net revenue from 2007-2011?

## Applying the Analytical Tool and Results

##### Question 1: Which Sales Organization has highest and lowest net revenue?
Following Figure represents a bar chart where x-axis shows net revenue for each sales organization shown in different colors. USA East has the highest net revenue while it is the least for USA West. Although, after combining the net revenues generated by USA East and USA West, the sum comes equal to the net revenues generated by Germany North and Germany South in combination i.e., approximately 120M USD for USA and 120M Euro for Germany.

##### Question 2: What is the trend observed for each of the sales organization in terms of their net revenue from 2007-2011?
Figure shows a Line Graph where x-axis represents Year and y-axis shows net Revenue. The graph shows that Germany has a positive trend overall in terms of net revenue, while for USA it has been declining till 2009. However, USA East was able to turn their net revenue up from 2009-2011 which matched the net revenue of Germany North in 2011 i.e., 14M approximately, whereas it dropped from 15M to approximately 7M in case of USA West.

## Analysis and Critique of the Tool

SAP HANA in-memory database helps the organization in decision making and advanced analytics. Because of its in-memory processing, it is very fast and provides real-time data analytics powered by machine learning.

Some advantages of using SAP HANA are that it is fully managed multi-cloud environment with seamless hybrid deployment (SAP, 2022). It provides a secure environment and hence assures full reliability to all the enterprises. Also, it allows quick performance, cost, and storage management. It uses a company’s data to streamline the processes, eliminate errors, and provide benefits to the users. Many operations can be parallelly processed in SAP HANA as opposed to single operation processing in traditional database systems.

Few limitations of SAP HANA are that it is only compatible to SAP or SUSE Linux certified hardware (IBM, 2022). It is a costly investment, and each time SAP makes an update the user needs to purchase it, which may be time consuming and costly. Also, as compared to other BI tools, its UI may be a bit outdated which makes it less preferrable.

## Conclusion:

Overall, it is good to learn about SAP HANA and know how to implement its environment for BI needs. It has in-memory database which makes it popular and demanding for organizations having enormous datasets. Personally, I did not face many issues in doing this lab. There are minute details which needs to be taken care of, otherwise you may get stuck in further processes. Since it is a relatively new environment so people might not be much comfortable with this, but I believe that with practice the errors will be manageable and easy to resolve.
