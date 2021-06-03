# Social Network API <!-- omit in toc -->
- [Description](#description)
- [User Story](#user-story)
- [Acceptance Criteria](#acceptance-criteria)
- [Submission Requirements](#submission-requirements)
## Description

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
- [ ] GitHub repo containing application code
- [ ] Walkthrough video dmeonstraing functionality of the application and all acceptance criteria beingn met
### Walkthrough Video - 37% <!-- omit in toc -->
- [ ] Shows all technical acceptance criteria being met
- [ ] Demonstrates starting the server
- [ ] Demonstrates following routes:
  - [ ] GET all users and all thoughts
  - [ ] GET single user and single thought
  - [ ] POST, PUT, DELETE a user and a thought
  - [ ] POST and DELETE user's friends
  - [ ] POST AND DELETE reactions to thoughts 
### Technical Acceptance Criteria - 40% <!-- omit in toc -->
- [ ] Uses Mongoose package to connect to a MongoDB database
- [ ] Includes User model
  - [ ] username: string, unique, required, trimmed
  - [ ] email: string, required, unique, must match valid email
  - [ ] thoughts: array of _id values referencing Thought model
  - [ ] friends: array of _id values referencing User model (self-reference)
  - [ ] SCHEMA: virtual called friendCount that retrieves length of user's friends array field on query
- [ ] Includes Thought model
  - [ ] thoughtText: string, required, between 1 and 280 characters
  - [ ] createdAt: date, default current timestamp, uses getter to format timestamp
  - [ ] username: string, required
  - [ ] reactions: array of nested documents created with the reactionSchema
  - [ ] SCHEMA: virtual called reactionCount that retrieves length of thought's reactions array field on query
- [ ] Includes Reaction schema
  - [ ] reactionId: uses ObjectId data type, default is new ObjectId
  - [ ] reactionBody: string, required, between 1 and 280 characters
  - [ ] username: string, required
  - [ ] createdAt: date, default current timestamp, uses getter to format timestamp
- [ ] API Routes
  - [ ] `/api/users` 
    - [ ] GET all users
    - [ ] GET single user by `_id` and populated thought and friend data
    - [ ] POST new user
    - [ ] PUT to update a user by `_id`
    - [ ] DELETE to remove user by `_id`
    - [ ] BONUS: remove a user's associated thoughts when deleted
  - [ ] `/api/users/:userId/friends/:friendId`
    - [ ] POST to add a new friend to user's friend list
    - [ ] DELETE to remove a friends from a user's friend list
  - [ ] `/api/thoughts`
    - [ ] GET all thoughts
    - [ ] GET single thought by `_id`
    - [ ] POST to create new thought (push created thought's id to user's thoughts array field)
    - [ ] PUT to update thought by its `_id`
    - [ ] DELETE to remove thought by its `_id`
  - [ ] `/api/thoughts/:thoughtId/reactions`
    - [ ] POST to create reaction stored in a single thought's reactions array field
    - [ ] DELETE to pull and remove a reaction by the reaction's reactionId value
- [ ] Formats queried timestamps properly
### Repository Quality - 13% <!-- omit in toc -->
- [ ] Has a unique name
- [ ] Follows best practices for file structure and naming conventions
- [ ] Follows best practices for class/id naming conventions, indentation, quality comments, etc.
- [ ] Contains multiple descriptive commit messages
- [ ] Contains high-quality README with description and link to walkthrough video