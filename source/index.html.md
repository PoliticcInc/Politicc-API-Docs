---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
# ruby
# python
# javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Politicc **Fact Check** API! You can use our API to access Politicc API endpoints, which can get information on various fact-checkers online including [FactCheck.org](https://factcheck.org), [Snopes](https://snopes.com), [PolitiFact](https://politifact.com), [Washington Post](https://washingtonpost.com), including our own at [Politi.cc](https://politi.cc/fact-check).


We currently only have the Shell language binding with Node.JS, Ruby, and Python on their way!


# Authentication

> To authorize, use this code:


```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: API_KEY"
```



> Make sure to replace `API_KEY` with your API key.

Politicc uses API keys to allow access to the API. You can register a new Politicc API key at our [developer portal](http://api.politi.cc/developers).

Politicc expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: API_KEY`

<aside class="notice">
You must replace <code>API_KEY</code> with your personal API key.
</aside>

# Fact Check

## Get All Fact Check


```shell
curl "http://api.politi.cc/v1/fact-check"
  -H "Authorization: API_KEY"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('API_KEY');
let fact-check = api.fact-check.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all fact-check.

### HTTP Request

`GET http://api.politi.cc/v1/fact-check`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
recent | true | If set to true, the result will also include fact-check.
org | mix | The slugified version of the organizations name. <br><br> **Options include**: `factcheck`, `snopes`, `politifact`, `washington-post`, `politicc` and `mix` that provides a the most current fact check articles
count | 10 | Number of fact check articles to return.

<aside class="success">
Remember — a happy fact-check is an authenticated fact-check!
</aside>

## Get a Specific Fact Check Article



```shell
curl "http://api.politi.cc/v1/fact-check/2"
  -H "Authorization: API_KEY"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific fact-check.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://api.politi.cc/v1/fact-check/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the fact-check to retrieve

## Advanced Query
```shell
curl "http://api.politi.cc/v1/fact-check?page=0&count=999&categories=[\"3 Pinocchios\",\"Immigration\",\"SKU\",\"CNN\"]&fields=[\"author\"]&sortBy=author"
  -H "Authorization: API_KEY"
```



> The above command returns JSON structured like this:

```json
{
    "pageSize": 10,//amount of items to return per page
    "total": 39,//total number of all items
    "page": 24,//current page index
    "lastPage": 4,//last page index
    "currentPageSize": 0,//items returned length
    "name": "companies", //name
    "data": []
}
```
# News TODO
/news/all
/news/company
/news/archive
/news/hot //default
//if(id==="all")data=µœ.data[0]//all
//else if(id==="company")data=µœ.data[1]//byCompany
//else if(id==="archive")data=µœ.data[2]//byDate
//else data=µœ.data[3]//Hot

```json
{
    "count": 70,
    "page": 0,
    "size": 4,
    "data": [
        {
            "author": "Bethania Palma"
        },
        {
            "author": "Glenn Kessler"
        },
        {
            "author": "Kim LaCapria"
        },
        {
            "author": "Michelle Ye Hee Lee"
        }
    ]
}
```
## Delete a Specific Fact Check Article





```shell
curl "http://api.politi.cc/v1/fact-check/2"
  -X DELETE
  -H "Authorization: API_KEY"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint retrieves a specific fact-check.

### HTTP Request

`DELETE http://api.politi.cc/v1/fact-check/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the fact-check to delete
