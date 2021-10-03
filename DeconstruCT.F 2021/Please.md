# Please Challenge Writeup (03/10/2021)
As the name suggests, this challenge requires you to adjust your requests according to the server in order to retrieve the flag. 

## 1. Examine the target
<img src=img/please1.png width=500px>

The target consists of a page asking you to provide an username.
Let's try a random one (cptee):

<img src=img/please2.png width=500px>

It seems that Clancy is the only username that can access the website.

## 2. Submit Clancy as the Username
When we submit Clancy as the username, a different error is shown:

<img src=img/please3.png width=500px>


That's is odd. Let's try analyzing our request with <b>Burp Suite</b>.

<img src=img/please4.png width=500px>

## 3. Admin_Access Flag

There is a flag called <b>Admin_Access</b> set as False.
Switch it to True and the following happens:

<img src=img/please5.png width=500px>

Seems like we have the wrong browser.
Refresh the page and send the request to Burp's Repeater.

## 4. User-Agent
Since the server will only accept requests from DeemaBrowser, by changing our User-Agent we can bypass this requirement.

<img src=img/please6.png width=500px>

Response: 

<img src=img/please7.png width=500px>

## 5. Basic Authentication
We have to provide an Authorization Header with "What'sTheMagicWord?" as the passphrase. Please add the header below to your request:

```
Authorization: Basic <credentials>
```

Substitute credentials to What'sTheMagicWord? base64 encoded

```
Authorization: Basic V2hhdCdzVGhlTWFnaWNXb3JkPw==
```

Response:

<img src=img/please8.png width=500px>

Seems like we also need to provide a date in order to access the files.

## 6. Date
Syntax
```
Date: <day-name>, <day> <month> <year> <hour>:<minute>:<second> GMT
```

Let's provide a date in April 2021 and analyze the response:
```
Date: Thu, 1 Apr 2021 12:00:00 GMT
```

<img src=img/please9.png width=500px>

Change the date to Monday, 5th of April:
```
Date: Mon, 5 Apr 2021 12:00:00 GMT
```

<img src=img/please10.png width=500px>

Retrieve the Flag and that's it!

Thank you for reading.













