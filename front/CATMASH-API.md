# catmash-api

---


**Get list of all cats**
----
  Returns list of all cats

* **URL**

  /cats

* **Method:**

  `GET`
  
*  **URL Params**

  None

* **Data Params**

  None

* **Success Response:**

  * **Code:** 200 OK <br />
    **Content:** 
```javascript
    [
        {
            "id": "catId",
            "score": 0,
            "url": "catUrl"
        },
        {
            "id": "catId",
            "score": 0,
            "url": "catUrl"
        },
        {
            "id": "catId",
            "score": 0,
            "url": "catUrl"
        }
    ]
```
 
* **Error Response:**

  * **Code:** 500 Internal Server Error <br />
    **Content:** `{ error : "Internal Server Error" }`

* **Sample Call:**

```javascript
    $.ajax({
      url: "http://api.catmash.latelier.co/cats",
      dataType: "json",
      type: "GET",
      success: function(r) {
        console.log(r);
      }
    });
```



**Create new cat**
----
  Create new cat

* **URL**

  /cats

* **Method:**

  `POST`
  
*  **URL Params**

   **Required:**
 
   `url=String`

* **Data Params**

  None

* **Success Response:**

  * **Code:** 201 CREATED<br />
    **Content:** 
```javascript
    {
        "id": "catId",
        "score": 0,
        "url": "catUrl"
    }
```
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** `{ error : "Bad Request" }`

  OR

  * **Code:** 409 CONFLICT <br />
    **Content:** `{ error : "Cat :_id already exist" }`

  OR 

  * **Code:** 500 Internal Server Error <br />
    **Content:** `{ error : "Internal Server Error" }`

* **Sample Call:**

```javascript
    $.ajax({
      url: "http://api.catmash.latelier.co/cats",
      dataType: "json",
      type: "POST",
      data: {url: "http://24.media.tumblr.com/tumblr_lr3t7tLxtH1qlyuwso1_1280.jpg"},
      success : function(r) {
        console.log(r);
      }
    });
```


**Get a new match**
----
  Returns a new match

* **URL**

  /match

* **Method:**

  `GET`
  
*  **URL Params**

  None

* **Data Params**

  None

* **Success Response:**

  * **Code:** 200 OK <br />
    **Content:** 
```javascript
    {
      "match": {
        "winnerId": null,
        "id": "matchId",
        "date": "yyyy-mm-ddThh:mm:ss.msZ",
        "cats": [
          {
            "id": "catId",
            "score": 0,
            "url": "catUrl"
          },
          {
            "id": "catId",
            "score": 0,
            "url": "catUrl"
          }
        ]
      }
    }
```
 
* **Error Response:**

  * **Code:** 500 Internal Server Error <br />
    **Content:** `{ error : "Internal Server Error" }`

* **Sample Call:**

```javascript
    $.ajax({
      url: "http://api.catmash.latelier.co/match",
      dataType: "json",
      type: "GET",
      success: function(r) {
        console.log(r);
      }
    });
```



**Set match score**
----
  Set the score of a match

* **URL**

  /match

* **Method:**

  `POST`
  
*  **URL Params**

   **Required:**
 
   `matchId=String`  
   `winnerId=String`

* **Data Params**

  None

* **Success Response:**

  * **Code:** 200 OK <br />
    **Content:** 
```javascript
    {
        "match": {
        "winnerId": "catId",
        "id": "matchId",
        "date": "yyyy-mm-ddThh:mm:ss.msZ",
        "cats": [
          {
            "id": "catId",
            "score": 1,
            "url": "catUrl"
          },
          {
            "id": "catId",
            "score": 0,
            "url": "catUrl"
          }
        ]
      }
    }
```
 
* **Error Response:**

  * **Code:** 400 BAD REQUEST <br />
    **Content:** `{ error : "Bad Request" }`

  OR

  * **Code:** 401 UNAUTHORIZED <br />
    **Content:** `{ error : "Match :matchId already voted" }`

  OR

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "Cat :winnerId not found in this match" }`

  OR 

  * **Code:** 404 NOT FOUND <br />
    **Content:** `{ error : "Match :matchId not found" }`

  OR 

  * **Code:** 500 Internal Server Error <br />
    **Content:** `{ error : "Internal Server Error" }`

* **Sample Call:**

```javascript
    $.ajax({
      url: "http://api.catmash.latelier.co/match",
      dataType: "json",
      type: "POST",
      data: {matchID: "592c1b699f3254001cff6387", winnerId: "592a0d9138b2641b4335b503"},
      success : function(r) {
        console.log(r);
      }
    });
```