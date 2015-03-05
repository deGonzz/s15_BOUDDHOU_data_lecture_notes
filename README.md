# Lecture Notes for Data Engineering in Spring 2015
## Lecture 1

Prof. Anderson is asking us to create a repo on Github and take notes in Markdown. 

### What about Big Data

Social Networks
Data Analytics - Storage
Data Sampling
---
---
Machine Learning
eg statistics is based on sampling. which method to use to get a sample? Big data can change the wau we use stat because we're not sampling. We're using the actual numbers.

### Storage

NoSql: optimizes queries you care about from unstructured schemas. 
Sql: Sql is good for schema that optimize queries that you're always interested in. 
e.g. see http://www.thegeekstuff.com/2014/01/sql-vs-nosql-db/
Data moedeling is "wicked" hard
(utf8, which Twitter uses, is better than ASCII to for instance show emojis - ASCII is too limited)

#### Technoogies
Document
Graph
Key-Value stores
Columnar

#### Infoviz (side effects)

### Data Lifecycle
Collection \ 
            Clean Up -> Storage <- -> Processing 
                        Analysis -> Query + Visualize + Act  
                                    ALL THIS LEADS TO QUESTIONS
Generation /

#### Question
Curation (prioritization of data source, which one gives most value?) \
                                                                        
Triage (prioritization of a situation)                                /
Paklrgfiygrci

### on Thursday: http requests (GET, POST, PUT, DELETE) - response cycles.

## Lecture 2

###Go to the wiki pages: 
https://github.com/cu-data-engineering-s15/syllabus/wiki/Test-Page
https://github.com/cu-data-engineering-s15/syllabus/wiki/Useful-Links
https://github.com/cu-data-engineering-s15/syllabus/wiki/Homeworks

###Presentation on Markdown form Taylor at this link:
https://github.com/taylordusting/s15_Taylor_markdown
It was preeeetty informative!

### RESTful terms
handler
request-response
index.html --> file on the srver disk
<img src=' '> --> link to another web addresss to load images
script tags

###REST (Representation-State-Transfer)
Envision the world to find rssources. We want to separate out the ressources and the different representations that it can take on
See URI resources (describe class and links larger than URL and are  abit more generic)
See CRUD (Create-Read-Update-Delete)

###Requests: on "/users"
GET: Give me a representation of all users. Or we can put an ID right next to it to get a specific user: "/users/id"
POST: Create a new user {data}
PUT: Update user
DELETE: Destroy a user

###Stepping through an example
See the Sinatra gem in the Ruby space
Also use the json gem
use curl http://localhost:3000/whattimeisit  to get a response (en l'occurence, the inside of the get converted into Json)

```ruby
require 'sinatra'
require 'sinatra/reloader' if development
require 'json'


configure do
	set :port, 3000
end

get '/api/1.0/whattimeisit' do
	{ status: true, message: Time.now }.to_json + "n\""
end
```

Check: https://github.com/cu-data-engineering-s15/contacts for next lecture implementation
Figure out: database? id? input? output? errors?


## Lecture 3

###RESTFUL WEB SERVICES
REST is an architecturqal style for web services
An approach to developing web services that mimic the design of the world wide web

###REST OPERATIONS
For each resource you can typically perform at least one of the folllowign CRUD (Create, read, Update Delete) opertaions:
####
POST
GET 
PUT
DELETE

###EXAMPLES (1)
```
GET /api/1.0/users
```
Retrieve a list of all users

```
GET /api/1.0/users/0
```
Retrieve the details of User 0

```
POST /api/1.0/users
```
Create a new user

##EXAMPLES (2)

```
PUT /api/1.0/users/0
```
Update user 0

```
DELETE /api/1.0/users/0
```
Delete user 0

```
GET /api/1.0/search?q=tattersail
```
Perform search with the query *tattersail*

###DISCUSSION (1)
####Each operation may produce a result:
With RESTful services, JSON format is king
####POST and PUT methods typically send data
Also in JSON format
May be in URL or int he body of the HTTP Request (eg for GET, the data may apear as query params)
###Other formats are possible: HTML and XML are typical
###If a request needs to be authenticated
The authentication data appears in HTTP headers

###DISCUSSION (2)
How do you think operations on two resources are handled?
####ONE APPROACH
```
GET /api/1.0/posts/0/comments/1
```
Get the first comment on post 10

```
POST /api/1.0/posts/0/comments
```
Create aew comment on post 0

###ISSUES
####Security: how do youdeal with authencticate users?
####Identity: how are ids assigned to resources?
####Failure: how do we handle failure situations?
	In the example today, I handle itin the JSON
	I could have used HTTP Status Codes (404, 500, etc.)
	Most services will use a combination of both
####Persistency: how are resources stored?
		
## Lecture 4

###Presentation on Git
###Presentation on Github via @zandrr
For next Lecture, make sure we have curl installed on our machine for the live challenge!!

## Lecture 5
###Presentation on Node.js by Ken

## Lecture 6
###Presentation on Express by Ken

## Lecture 7
###Presentation on Angular.js by Ken

## Lecture 8
###More on Angular.js by Ken

## Lecture 9
###Presentation on getting data from Twitter by Ken
Going over this page on Angular: https://gist.github.com/kenbod/be0c9ce0a79bcd342465
Recommended reading: *The Principles of Object-Oriented JavaScript*, *Secrets of the JavaScript Ninja*
Link1: http://netcraft.co.il/fedia/books/SecretsoftheJavaScriptNinja.pdf
Link2: http://it-ebooks.info/book/4449/

###Contacts Web App: https://github.com/cu-data-engineering-s15/contacts_web_app
###For the Twitter API:
Go to: https://dev.twitter.com/
Start a "Ken's Test App" Twitter app at: https://apps.twitter.com/app/7906727/keys
Check out the documentation's REST API: https://dev.twitter.com/rest/public
Check out the documentation's Streaming API: https://dev.twitter.com/streaming/overview

## Lecture 10 
### Getting Data from Twitter Take Two
Open: file:///Users/Louis/Documents/SCHOOL/DATAENG/lecture_10-gh-pages/index.html
Check out: https://stedolan.github.io/jq/  that pretty prints JSON
Check out: https://dev.twitter.com/rest/public/timelines
Check out: https://github.com/cu-data-engineering-s15/syllabus/wiki/Topics  to find a topic to present for the class

## Lecture 11
### Twitter Data Collection Framework

## Lecture 12
### Introduction to NoSQL by Ken

## Lecture 13
### CouchDB by Ken
####CAP Theorem: pick any two
Consistency
Availability
Partition Tolerance
####CouchDB chooses Avalability and Partition Tolerance
####Structures used:
B-trees
MapReduce
No Locking
Validation
Incremental Replication
####curl command
$ couchdb
$ curl http://127.0.0.1:5984/curl http://127.0.0.1:5984/
$ curl -X GET http://127.0.0.1:5984/_all_dbs
$ curl -X PUT http://127.0.0.1:5984/tweets
$ curl -X GET http://127.0.0.1:5984/_all_dbs
$ curl -X PUT http://127.0.0.1:5984/delete_me
Then checkout: http://127.0.0.1:5984/_utils/
Checkout couchdb actual online web client
####Updating a page with couchdb
When going through couchdb, checkout revision ID vs trueID when updating a page

## Lecture 14
### MongoDB Presentation by Vikas 
####Terminology
Document
Collection
Independent databases

## Lecture 15
### Getting help on assignment 3

## Lecture 16
### Overview on importing tweets to MongoDB
