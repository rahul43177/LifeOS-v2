## Agenda
![[../../../attachments/02 - Node.js - Rest API and Express - agenda.png]]

## To Learn 
> [!question]- To Learn later
> 1. HTTP Verbs 
> 2. Protocols and all in the API 
> 3. GRPC , SDK , windows API 
> 4. REST in detail 


## What is an API ? 
In simple terms : 
IT is a contract between two systems
![[../../../attachments/02 - Node.js - Rest API and Express - api notes.png]]


## REST  
[Rest Medium Article guide](https://medium.com/@sarthakbhatkar/rest-api-fundamentals-a-begginers-guide-efc0cf51da75)
### What is REST ?  
It is basically an API with some set of principles. 
It is basically :
- Architectural style for designing networked applications
- Uses HTTP protocol for client-server communication
- Treats server-side data as resources that can be accessed and modified
'

 
REST talks about some standard principles of writing APIs  
![[../../../attachments/02 - Node.js - Rest API and Express - rest.png]]
![[../../../attachments/02 - Node.js - Rest API and Express - rest2.png]]
The data can be in `XML and HTML` as well , not always in the form of `JSON`

### Key principles of REST 
1. Stateless
2. Client Server Architecture - REST is mostly used in the Client server architecture.

![[../../../attachments/02 - Node.js - Rest API and Express - REST API architecture.png]]
![[../../../attachments/02 - Node.js - Rest API and Express - request example.png]]
![[../../../attachments/02 - Node.js - Rest API and Express - REST API response example.png]]

### HTTP Status Codes
![[../../../attachments/02 - Node.js - Rest API and Express - HTTP codes.png]]

### RESTful endpoint structure
![[../../../attachments/02 - Node.js - Rest API and Express - restful endpoint structure.png]]


## Coding and Hands on - REST
### Course Rating Service
- Write REST APIs 
	- List all courses
	- Get details of a course 
	- Update a course 
	- Get rating of a course 
	- Fetch all registered users of a course 

#### Assumptions 
`serviceName : course-rating-service`
versions : v1 

## Path Parameters vs Query Parameters
Study -- [[Path Parameter]]
### [[Query Parameters]]

### When to Use What?

**Use Path Parameters for:**

- Resource identification
- Required information
- Hierarchical data
- RESTful resource access

```
/users/123
/posts/456/comments/789
/api/v2/products/abc
```

**Use Query Parameters for:**

- Filtering results
- Sorting/ordering
- Pagination
- Optional parameters
- Search queries

```
/users?role=admin&active=true
/products?sort=price&order=desc
/posts?page=2&limit=20
/search?q=nodejs&category=tutorial
```

### Combined Usage

```javascript
// Route with both
app.get('/users/:id/posts', handler)

// URL
GET /users/123/posts?sort=date&limit=10

// Access
req.params.id  // "123"
req.query.sort // "date"
req.query.limit // "10"
```

### Best Practices

- Path params: nouns identifying resources
- Query params: adjectives describing/filtering resources
- Keep URLs readable and intuitive
- Use path params for core resource structure
- Use query params for optional modifications

## Query parameter  
[[Query Parameters]]

## Pagination 
- We pass the limit and offset in the query params 
- Express will read that in the key value pair. 
- So basically express is doing all the heavy lifting for us and then if we give the query params like : `localhost:3000/courses?limit=10&offset=2`
- `consoe.log(req.query)`  ->  `{ limit : '1' , offset : '2'}`
- So this will in the express give us ![[../../../attachments/03 - Node.js - Rest API and Express - Part 2 - query params.png]]

## Middleware 
POST and PUT and PATCH 

## Environment variable - `process.env`
![[../../../attachments/03 - Deep Dive into Async Programming - process.env.png]]
So here in the server starting we are sending `PORT = 3000 node app.js`

so this PORT variable can be read through -> `runningPORT = process.env.PORT`
so we will get that value in `runningPORT`

This was the case for the single variable called PORT 
But in an actual application we have a lot of variable which we don't want to expose in the codebase so that time when the variables are huge , we create a hidden file called - `.env`

> Any file starting with dot (.) means hidden

### Importing env and using it 
Now let's create a dot env file so for accessing env variables we have a package in express -> `dotenv`

so we have to write -> 
`require('dotenv').config()`

or 

`require('dotenv').config({path: __dirname + '/.env'})`
you can give path as well 


and then we can import in our project like : 
```js 
const PORT = process.env.PORT //whatever the name you have given in the env file 
```


## Folder and file structures 
- we kept the logging system in the `middleware/loggingMechanism`
- routes in different folder 
- controller in different 
- basically the separation of files and folder 

### Router folder how teacher has written : 
![[../../../attachments/03 - Deep Dive into Async Programming  - routerLogic.png]]
### Controller 
- simple API functions and importing the database model  



## Assignment
[[Express and RestAPI assignment]]
