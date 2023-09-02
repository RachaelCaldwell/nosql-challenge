# NoSQL-Challenge
The Module 12 NoSQL Challenge is divided into 3 parts:
* Database and Jupyter Notebook Setup
* Update the Database
* Exploratory Analysis

The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. This challenge evaluates ratings data to help journalists, food critics, and editors of a food magazine, Eat Safe, Love decide where to focus future articles.

**Part 1: Database and Jupyter Notebook Setup**<br>

Part 1 uses the [NoSQL_setup_starter.ipynb](Starter_Code/NoSQL_setup_starter.ipynb) to complete the following tasks:
* Import the data provided in the establishments.json file from the Terminal
* Name the database uk_food and the collection establishments
* Copy the text used to import the data from the Terminal to a markdown cell in Jupyter notebook
* Within the notebook, import the libraries: PyMongo and Pretty Print (pprint)
* Create an instance of the Mongo Client
* Confirm the created the database and loaded data
* List the databases in MongoDB
* Confirm that uk_food is listed
* List the collection(s) in the database to ensure that establishments is there
* Find and display one document in the establishments collection using find_one and display with pprint
* Assign the establishments collection to a variable to prepare the collection for use

**Part 2: Update the Database**<br>
Part 2 uses the [NoSQL_setup_starter.ipynb](Starter_Code/NoSQL_setup_starter.ipynb) file where the magazine editors requested modifications to the database. The following changes were made to the establishments collection:
* The supplied data for the "Penang Flavours" restaurant is inserted into the establishments collection
* A query is performed to find the BusinessTypeID for "Restaurant/Cafe/Canteen" and returns only the BusinessTypeID and BusinessType fields
* The "Penang Flavours" document is updated with the correct value for BusinessTypeID
* A query is correctly performed to delete all the documents in the collection where "Dover Local Authority" is the value for LocalAuthorityName
* A count_documents() check is performed before and after the removal of the Dover documents to ensure the documents were removed
* An update_many() query is performed to convert the latitude and longitude fields from strings to decimal numbers and RatingValue to integers

**Part 3: Exploratory Analysis**<br>
Part 3 uses the [NoSQL_analysis_starter.ipynb](Starter_Code/NoSQL_analysis_starter.ipynb) file to answer specific questions for Eat Safe, Love in order to find the locations they wish to visit and avoid.

**Question 1: Which establishments have a hygiene score equal to 20?**
* A query is performed to find the establishments with a hygiene score of 20
* count_documents() is used to list the correct number of documents (answer: 41)
* The first result is printed using pprint
* The results are converted to a Pandas DataFrame and displayed
![image](https://github.com/RachaelCaldwell/nosql-challenge/blob/main/Starter_Code/Images/hygeine_df.png)

**Question 2: Which establishments in London have a RatingValue greater than or equal to 4?**
*A query is performed to find the establishments in London with a RatingValue greater than or equal to 4
* The query uses the $regex operator to locate the London establishments
* count_documents() is used to list the correct number of documents (answer: 33)
* The first result is printed using pprint
* The results are converted to a Pandas DataFrame and displayed
![image](

**Question 3: What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?**
* A query is performed to find the establishments within 0.01 degree of the "Penang Flavours" restaurant
* The query limits the results to establishments with a RatingValue of 5
* The query uses the sort() method in PyMongo to sort in ascending order on the hygiene score
* The query uses the limit() method in PyMongo to limit the results to 5
* All five results are printed using pprint
* The results are converted to a Pandas DataFrame and displayed
![image}(

**Question 4: How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.**
* An aggregation pipeline is built to include a match query, group, and sort
* The match query matches documents with a hygiene score of 0
* The group step of the pipeline is grouped on LocalAuthorityName and counts the number of documents
* The sort step of the pipeline sorts the count of the documents in descending order
* The aggregation pipeline is correctly sent to the aggregate() method
* The results from the aggregation query is cast as a list and then saved to a variable
* The first ten results are printed using pprint
* The results are converted to a Pandas DataFrame and displayed
![image}(
