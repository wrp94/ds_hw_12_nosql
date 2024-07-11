# ds_hw_12_nosql

## Homework for Module 12 - NoSQL

In this assignment, I loaded data into a MongoDB collection, cleaned it, and used it for a quick analysis.

## Deliverables

### [Set Up](food_ratings/NoSQL_setup.ipynb)

To set up for this notebook, a local MongoDB server is required and the database needs to be imported.
This can be done using MongoImport from the terminal:

```shell
mongoimport --type json -d uk_food -c establishments --drop establishments.json
```

Once the data is loaded, the notebook connects to the local MongoDB server to update and clean the data.

#### Updating/Cleaning Data

- A new restaurant is added and the `BusinessTypeID` field is updated using existing data from the database.

- Since the client is uninterested in establishments from Dover, documents with that `LocalAuthorityName` are dropped.

- `latitude` and `longitude` values are converted to decimal numbers from strings.

- `RatingValue` has non-numeric values turned to null and all numeric values converted to integers from strings.

### [Analysis](food_ratings/NoSQL_analysis.ipynb)

This notebook connects to the database and tries to answer four questions by querying the data and returning Pandas DataFrames:

1) Which establishments have a hygiene score equal to 20?
    - The first result is "The Chase Rest Home".

2) Which establishments in London have a `RatingValue` greater than or equal to 4?
    - There are 33 establishments.
    - The first one is named "Charlie's"

3) What are the top 5 establishments with a `RatingValue` of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
    1) Folkstone Trawlers Shop
    2) The Club Hut
    3) Docker
    4) St. Mary's COE (aided) Primary School
    5) Mariner

4) How many establishments in each Local Authority area have a hygiene score of 0?
    - Thanet has the most, with 1130 establishments.
    - The next closest is Greenwich with 882 establishments.
