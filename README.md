# Social Network API <!-- omit in toc -->
- [Description](#description)
- [Demo](#demo)
- [Installation](#installation)
- [User Story](#user-story)
- [Acceptance Criteria](#acceptance-criteria)
- [Submission Requirements](#submission-requirements)
## Description
The social network api is a complete RESTful API using MondoDB with the Mongoose framework. With the api, users can perform all the relevant CRUD API calls for the Users and Thought models, the basis for a social media application.

MongoDB gives the application the flexibility to grow without the worry of outdating older data through schema updates. The NoSQL database structure allows for any data to be stored within a document, but this flexibility often comes with the cost of duplicated data and possibly inconsistent data across databases.

## Demo
A demonstration video of the API in use can be found [here](https://www.youtube.com/watch?v=gP6sAokOFhY).

## Installation
 - clone repository to local machine
 - run `npm i` from the command line in the root directory to download the required dependencies
 - run `npm start` to start the server
 - use an API testing software to run API calls or run the calls throught the browser (the default server location is localhost:3001)

## User Story
```
AS A social media startup
I WANT an API for my social network that uses a NoSQL database
SO THAT my website can handle large amounts of unstructured data
```

## Acceptance Criteria
```
GIVEN a social network API
WHEN I enter the command to invoke the application
THEN my server is started and the Mongoose models are synced to the MongoDB database
WHEN I open API GET routes in Insomnia Core for users and thoughts
THEN the data for each of these routes is displayed in a formatted JSON
WHEN I test API POST, PUT, and DELETE routes in Insomnia Core
THEN I am able to successfully create, update, and delete users and thoughts in my database
WHEN I test API POST and DELETE routes in Insomnia Core
THEN I am able to successfully create and delete reactions to thoughts and add and remove friends to a user’s friend list
```

## Submission Requirements
### Deliverables - 10% <!-- omit in toc -->
- [x] GitHub repo containing application code
- [x] Walkthrough video dmeonstraing functionality of the application and all acceptance criteria beingn met
### Walkthrough Video - 37% <!-- omit in toc -->
- [x] Shows all technical acceptance criteria being met
- [x] Demonstrates starting the server
- [x] Demonstrates following routes:
  - [x] GET all users and all thoughts
  - [x] GET single user and single thought
  - [x] POST, PUT, DELETE a user and a thought
  - [x] POST and DELETE user's friends
  - [x] POST AND DELETE reactions to thoughts 
### Technical Acceptance Criteria - 40% <!-- omit in toc -->
- [x] Uses Mongoose package to connect to a MongoDB database
- [x] Includes User model
  - [x] username: string, unique, required, trimmed
  - [x] email: string, required, unique, must match valid email
  - [x] thoughts: array of _id values referencing Thought model
  - [x] friends: array of _id values referencing User model (self-reference)
  - [x] SCHEMA: virtual called friendCount that retrieves length of user's friends array field on query
- [x] Includes Thought model
  - [x] thoughtText: string, required, between 1 and 280 characters
  - [x] createdAt: date, default current timestamp, uses getter to format timestamp
  - [x] username: string, required
  - [x] reactions: array of nested documents created with the reactionSchema
  - [x] SCHEMA: virtual called reactionCount that retrieves length of thought's reactions array field on query
- [x] Includes Reaction schema
  - [x] reactionId: uses ObjectId data type, default is new ObjectId
  - [x] reactionBody: string, required, between 1 and 280 characters
  - [x] username: string, required
  - [x] createdAt: date, default current timestamp, uses getter to format timestamp
- [x] API Routes
  - [x] `/api/users` 
    - [x] GET all users
    - [x] GET single user by `_id` and populated thought and friend data
    - [x] POST new user
    - [x] PUT to update a user by `_id`
    - [x] DELETE to remove user by `_id`
    - [x] BONUS: remove a user's associated thoughts when deleted
  - [x] `/api/users/:userId/friends/:friendId`
    - [x] POST to add a new friend to user's friend list
    - [x] DELETE to remove a friends from a user's friend list
  - [x] `/api/thoughts`
    - [x] GET all thoughts
    - [x] GET single thought by `_id`
    - [x] POST to create new thought (push created thought's id to user's thoughts array field)
    - [x] PUT to update thought by its `_id`
    - [x] DELETE to remove thought by its `_id`
  - [x] `/api/thoughts/:thoughtId/reactions`
    - [x] POST to create reaction stored in a single thought's reactions array field
    - [x] DELETE to pull and remove a reaction by the reaction's reactionId value
- [x] Formats queried timestamps properly
### Repository Quality - 13% <!-- omit in toc -->
- [x] Has a unique name
- [x] Follows best practices for file structure and naming conventions
- [x] Follows best practices for class/id naming conventions, indentation, quality comments, etc.
- [x] Contains multiple descriptive commit messages
- [x] Contains high-quality README with description and link to walkthrough video