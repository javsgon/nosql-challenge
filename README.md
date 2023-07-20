# NO SQL Challenge
## Instructions
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. I've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

## Part 1: Database and Jupyter Notebook Set Up
I used NoSQL_setup_starter.ipynb for this section of the challenge.

1- Imported the data provided in the establishments.json file from my Terminal. Named the database uk_food and the collection establishments. Copied the text I used to import my data from myTerminal to a markdown cell in my notebook.

2- Within my notebook, imported the libraries needed: PyMongo and Pretty Print (pprint).

3- Created an instance of the Mongo Client.

4- Confirmed that I created the database and loaded the data properly:

- Listed the databases I had in MongoDB. Confirmed that uk_food is listed.
- Listed the collection(s) in the database to ensure that establishments is there.
- Found and displayed one document in the establishments collection using find_one and display with pprint.

5- Assigned the establishments collection to a variable to prepare the collection for use.

## Part 2: Update the Database
I used NoSQL_setup_starter.ipynb for this section of the challenge.

The magazine editors have some requested modifications for the database before I can perform any queries or analysis for them. Make the following changes to the establishments collection:

1- An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked me to include it in the analysis. Added the following information to the database:

<img width="493" alt="Penang" src="https://github.com/javsgon/nosql-challenge/assets/125521896/fcd211ff-bdfe-4eeb-8986-81939819d09e">

2- Found the BusinessTypeID for "Restaurant/Cafe/Canteen" and returned only the BusinessTypeID and BusinessType fields.

3- Updated the new restaurant with the BusinessTypeID.

4- The magazine is not interested in any establishments in Dover, so I checked how many documents contained the Dover Local Authority. Then, I removed any establishments within the Dover Local Authority from the database, and checked the number of documents to ensure they were deleted.

5- Some of the number values are stored as strings, when they should be stored as numbers.

1. I used update_many to convert latitude and longitude to decimal numbers.
2. I used update_many to convert RatingValue to integer numbers.

## Part 3: Exploratory Analysis
Eat Safe, Love has specific questions they wanted me to answer, which will help them find the locations they wish to visit and avoid.

I used NoSQL_analysis_starter.ipynb for this section of the challenge.

Some notes to be aware of while exploring the dataset:

- RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.
  - Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.

- The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.

I used the following questions to explore the database, and find the answers, so I can provide them to the magazine editors.

Unless otherwise stated, for each question:

- Used count_documents to display the number of documents contained in the result.

- Displayed the first document in the results using pprint.

1. Converted the result to a Pandas DataFrame, printed the number of rows in the DataFrame, and displayed the first 10 rows.

2. Which establishments have a hygiene score equal to 20?

3. Which establishments in London have a RatingValue greater than or equal to 4?

4- What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

5- How many establishments in each Local Authority area have a hygiene score of 0? I sorted the results from highest to lowest, and printed out the top ten local authority areas.
