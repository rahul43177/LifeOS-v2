---
feature: ../../../attachments/01 - Introduction to Web development and Backend Engineering - instructor.png
---
## Course Slides notes : 
MIRO Board : https://miro.com/app/board/uXjVJ_f_z2g=/?focusWidget=3458764642923732581
## Instructor :
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - instructor.png|500]]

## Agenda of today
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - agenda today.png|600]]

## How the web works ?
#### Client server architecture - [[../01 - Pre-Course Module/The Client-Server Model - A Deeper Understanding|The Client-Server Model - A Deeper Understanding]]

Think of this like ordering food at a restaurant. 
We have : 
1. Client 
2. Server 
These two communicate with each other. 
Client : The client is like me , the customer. In web terms , the client is typically web browser.
Client sends a request and a response comes from the server. 
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - client server.png|600]]

> ***So when we type google dot com in the browser***


#### DNS Resolution
the request will go to the the DNS 

request -> DNS -> send the request to ROOT name server 
There are total 13 root name server -> managed by 12 organisation 

So the flow right now 

mail.google.com -> DNA Resolution -> Root name server 

The complete picture look like this : [[01 Backend - DNS Resolution]]

we can check what happens when we hit : 
```plain text
dig + trace mail.google.com
```


## Backend Concepts 
### Frontend vs Backend
So let's say we have a form where we have 
	name 
	phone
there is <font color="#c0504d">button</font> to submit. 

![[../../../attachments/01 - Introduction to Web development and Backend Engineering - frontendvsbackend.png|600]]

### Request 
Things which can be there in the reqeust : 
	urls 
	headers 
	body/payload
	auth token
	parameters

The request looks somethings like this : [[01 - Backend - Request]]

![[../../../attachments/Client server architecture - HTTP request.png|600]]
### HTTP Methods : 
These are different ways by which we communicate with the servers.
1. <font color="#00b0f0">POST</font> -> Create a new record. 
2. <font color="#00b0f0">GET</font> -> Fetching the information 
3. <font color="#00b0f0">PUT</font> -> Update complete record -> replace the current object. and hence it can also be used to create 
4. <font color="#00b0f0">PATCH</font> -> Update smaller part of record in DB 
5. <font color="#00b0f0">DELETE</font> -> Delete the request in DB
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - HTTP request methods.png]]

### Response 
Things we will have here : 
	Status Code 
	Header 
	Payload / Data 
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - response.png|600]]


### HTTP Status Code 
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - status code.png|600]]

`1xx` -> Information code 
`2xx` -> Success codes
`3xx` -> Redirection codes
`4xx` -> Client error codes
`5xx` -> Server Errors codes
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - HTTP status codes.png|650]]




### Authentication and Authorisation 
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - auth.png|600]]
#### Authentication 
1. Who you are ? 
2. What is your identity ? 
3. Username / password || OAuth || 2 factor authentication || OTP verification 

#### Authorisation 
1. What are the things you are allowed , for example admins have more power in some website , so they are authorised. 
2. So basically how much power you have 

### CORS
Cross origin resource sharing
![[../../../attachments/01 - Introduction to Web development and Backend Engineering - cors.png|650]]
#### Main Concepts:
**CORS** - Cross Origin Resource Sharing
- The server is configured with CORS settings that control which domains are "allowed"
- There's a list of allowed domain names
**Same Origin Policy:**
- When a user visits `www.mybank.com` (logged in with authentication info/auth token)
- A script from `abc.com` tries to access resources
- The browser checks if `mybank.com` is in the allowed list:
    - If `mybank.com → allowed` ✓
    - If `xxx → disallowed` ✗
#### The Security Flow:
1. Server has CORS configuration with allowed domains
2. User is logged into mybank.com with auth credentials
3. A script from another domain (abc.com) attempts to make a request
4. The browser enforces the same-origin policy by checking CORS headers
5. Access is granted or denied based on whether the requesting domain is in the allowed list

This is a fundamental web security mechanism that prevents malicious websites from making unauthorised requests to other sites using your credentials. Without CORS/same-origin policy, a malicious script on abc.com could potentially access your bank account data while you're logged in.





### Things to learn today 
> ***Things to learn and read*** : 
- [ ] Difference between POST and PUT ? 
- [ ] When to use PUT and when to use POST ? 
- [ ] PUT is idempotent , what does it mean ? 
- [ ] Study about auth in detail 
- [ ] Read about CORS and same origin policy

[[Difference between POST and PUT]]
