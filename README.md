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
