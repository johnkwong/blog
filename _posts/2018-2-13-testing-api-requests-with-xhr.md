---
layout: post
title: Testing API Requests With XHR
tags: [other]
---
It is easy to test api service with XHR. Just open Chrome Console and enter XHR syntax to test it.
Sending HTTP GET request
```
var request = new XMLHttpRequest();
var url = 'https://abc.com/api/v1/product/' + id ;
request.open('GET', url, true);
request.send();
```
Sending HTTP POST request
```
POST Method
var request = new XMLHttpRequest();
var url = 'https://abc.com/api/v1/product/' ;
request.open("POST", url);
request.send();
```

GET Method with Header
```
var request = new XMLHttpRequest();
var url = 'https://abc.com/api/v1/product/' + id ;
request.open('GET', url, true);
request.setRequestHeader("Authorization", "Bearer " + access_token);
request.send();
```
POST Method with Header
```
POST Method
var request = new XMLHttpRequest();
var url = 'https://abc.com/api/v1/product/' ;
request.open("POST", url);
request.setRequestHeader("Content-Type", "application/json");
request.send();
```
