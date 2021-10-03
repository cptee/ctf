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

There is a flag called Admin_Access set as False.
Switch it to True and the following happens:








<style>
img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 500px;
    margin-top: 40px;
    margin-bottom: 40px;
}
</style>