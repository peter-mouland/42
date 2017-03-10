# Cross Origin Resource Sharing
### Chris Mckenzie
Principal Software Engineer - notonthehighstreet.com

---
# What is CORS?

> ## ~~It's when you add `Access-Control-Allowed-Headers: *` to all the requests and then the site works~~

>## A standard that permits the browser to circumvent restrictions enforced by the Same Origin Policy

---
# Same Origin Policy

>## Restricts how a resource from one origin can interact with resources from another origin (js, css, images, html)

## Origin = protocol + fully qualified domain + port

---
# Same Origin
## https://www.mywebsite.com/index.html
## https://www.mywebsite.com/fonts/myfont.ttf
## https://www.mywebsite.com/js/main.js
## https://www.mywebsite.com/css/styles.css

---
# Cross-Origin
## http://www.mywebsite.com/index.html
## http://www.mywebsite.com:3000/index.html
## https://www.mywebsite.com/fonts/myfont.ttf
## https://store.mywebsite.com/js/main.js
## https://www.hacker.com/css/styles.css

---
# Same Origin Policy restrictions
## Cannot read contents of cross-origin resource
## Can execute cross-origin resource
## Can partially send to cross-origin resource

---
# Cross Origin Read - Dangers

## Secure banking system 
https://www.yourbank.com/account_info.html


## Dodgy website
https://www.free-iphones.com
`<iframe src="https://www.yourbank.com/account_info.html"/>`
`document.getElementByThing('iframe').contentWindow.document.body.innerHTML`

---
# Cross Origin Execute - No Big Deal
## Secure banking system 
https://www.yourbank.com/account_info.html


## Dodgy website
https://www.free-iphones.com
`<iframe src="https://www.yourbank.com/account_info.html"/>`
## So what, I can see my own account information

---
# Cross Origin Send
- GET (with query params) 
- POST
## Permitted if there are no custom headers
## Server handles request as normal
## Forbidden from reading the response data
## Only allowed for legacy reasons

---
# Cross Origin Send
- PUT
- DELETE
## Not permitted


---
# Circumventing SOP with CORS

## Sometimes...
### Trusted domains have resources they want to share
### Domains which we own which need to interact

---
# Allow everybody to _read_ resource
## https://www.gov.uk/bank-holidays.json

### Executing this resource in the browser is not useful

### Reading the resources allows us to work with the data
Resource can set a Response Headers permitting any Origin to read the resource.

`Access-Control-Allow-Origin: *`

---
# Allow friends only to _read_ resource
## https://www.my-website.com/widget.html

### We want to embed the widget into a friendly webpage
`<iframe src="https://www.my-website.com/widget.html"/>`
```
widget = document.getElementByThing('iframe').contentWindow;
widget.secretFriendsOnlyData;
widget.doSomething();
```

### Allow the requesting origin exactly (no multiple values)
`Access-Control-Allow-Origin: https://www.friends.com`

---
# Sending data to cross-origin resource
- ### Get, Post with custom headers (via Ajax)
- ### Put, Delete

## Browser verifies with the server if a cross-domain request is permitted from the domain

`DELETE https://www.mywebsite.com/database` warrants a check...

---
# Sending data - The Preflight Request
### Browser makes an OPTION request to the resource
`OPTION https://www.mywebsite.com/database`
### Sets headers describing the request we wanted to make

```
Origin: https://www.otherdomain.com
Access-Control-Request-Method: DELETE
Access-Control-Request-Headers: X-Custom-Header
```

### No request body is sent

---
# Sending data - The Preflight Response
### The server sends a response describing what the resource permits in the headers

```
Access-Control-Allow-Origin: https://www.otherdomain.com
Access-Control-Allow-Methods: GET,PUT,POST,DELETE,OPTIONS
Access-Control-Allow-Headers: X-Custom-Header
```

### If the response permits the request, the browser proceeds to make the real request
### If there is no response or the request is not allowed it is aborted

---
# Adding Cookies 
## Ajax requests by default do not send cookies
## To send cookies: `xhr.withCredentials = true`
## Will require a pre-flight request to be made

## Must respond with: 
## `Access-Control-Allow-Credentials: true`

---
# Summarising
## Same Origin Policy keeps us safe
## CORS allows us to relax security when needed
## Think about _resources_ and _origins_
## Think _read, write(send), execute_
## Not only browsers make requests

---
# Questions?