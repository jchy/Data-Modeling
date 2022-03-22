# DATA MODELING

### PROBLEMS:~
- 1. What are valid ways to represent this one-to-many relationship in MongoDB?
- 2. What are valid ways on modelling many-to-many relationship with MongoDB?
- 3. What are valid ways to represent a one-to-one relationship with the document model in MongoDB?
- 4. create an ERD / CRD diagram for a blog application
- 5. create and design schema for each collection
- 6. Write a requirement document for designing a system like LinkedIn.
- 7. Estimate daily read and writes, users, data transfer, list down all assumptions you have made
- 8. Write down some queries ( no need to write actual queries, but the kind of information that 
- 9. users, and admins would like to see ). for example: - list 10 post by user_id with pagination descending order of date

### SOLUTIONS :~
- 1. There are several different ways to model 1:N relationship. 
-     i. Main three ways of them are 
-       a. Embedding
-       b. Linking
-       c. Bucketing

- 2. There are several different ways to model N:M relationship. 
-     i. Main two ways of them are 
-       a. One way Embedding
-       b. Two way Embedding

- 3. There are several different ways to model 1:1 relationship. 
-     i. Main two ways of them are 
-       a. Embedding
-       b. Linking

4. ERD (Entity Relationship Diagram) for blog post:~
- The fields that we will choose for createing a blog post are : ~
- i. title
- ii. subtitle
- iii. description
- iv. hash tags
- v. author
- vi. comment_text
- vii. comment_autor
- viii. comment_created_at
- ix. post_creation_date

- Here you will choose linking over the embedding beacuase a post might have 1000s of comments which may exceed the 16MB limit per document of MongoDB., so it is not preferable to embedding the comments with the post details
- So you will create 2 collections namely 
- 1. post
- 2. comments
-  We will link them throuh a foregin key

- 5. Blog Post Document
```js
  {
    _id: 1,
    title:"",
    subtitle:"",
    description:"",
    hashtags:"",
    author:"",
    created_at:""
  }
```
- Comment document with foreign keys
```js
  {
    blog_id: 1
    comment_text:"",
    comment_author:"",
    comment_created_at:""
  }
```
- NOTE : We can also consider bucketing to prevent the scenarios like if we have 1000 comments on a blog post, we would need to retrieve all 1000 documents causing a lot of reads from the database.
- Bucketing will also help a lot if we want pagination in the comment section

6. Requirement documents for designing a system like Linkedin
- We have to create many documents for a system like linkdin
- 1. users
- 2. posts
- 3. comments


