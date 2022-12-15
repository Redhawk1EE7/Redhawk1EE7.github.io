---
layout: post
title: Who are you?
date: 2022-12-14 18:40:00 -500
categories: [Writeups, picoCTF, Web]
tags: [web, writeup, easy]
---

# Overview
***Author: MADSTACKS*** 
___________________
## Challenge Description
***Let me in. Let me iiiiiiinnnnnnnnnnnnnnnnnnnn*** 
___________________
## Challenge Hints
***1. It ain't much, but it's an RFC https://tools.ietf.org/html/rfc2616***

## Challenge Page
![[Challenge Page]](https://github.com/Redhawk1EE7/Redhawk1EE7.github.io/blob/main/_posts/_img/picoCTF/who-are-you/1.png?raw=true "Challenge Page")

# Walkthrough
## BEFORE WE START!!

## Starting Point
After looking around the source code, the best thing we can start from is the hint provided for us: "***Only people who use the official PicoBrowser are allowed on this site!***". Thus we will go immediatly to fire **Burp Suite** & play around with the **HTTP Headers**.
*I'll consider that you have already set up your Burp, if not I suggest that you check one of the available guide on the internet, it is highly recommended to have Burp Suite by your side when doing Web stuff..* 

## Divining In
1. Starting by refreshing the page & grabbing the challenge `GET` request through the **HTTP History** panel and sending it to the **Repeater**. (You're free to use the Intercept button too.. xd)

![[Step 1]](https://github.com/Redhawk1EE7/Redhawk1EE7.github.io/blob/main/_posts/_img/picoCTF/who-are-you/2.png?raw=true "Interception")

2. We will start by changing the `User-Agent` value with "**PicoBrowser**" as follows:
```
User-Agent: PicoBrowser
```
![[Step 2]](https://github.com/Redhawk1EE7/Redhawk1EE7.github.io/blob/main/_posts/_img/picoCTF/who-are-you/3.png?raw=true "User-Agent")

3. In the response we can see that we seem as we are visiting from another site thus we will use another **HTTP Header** called `Referer` with a value of the our Host:
```
Referer: mercury.picoctf.net:1270 
```
4. "**Sorry, this site only worked in 2018.**", let's counter that with a simple `Date` **HTTP Header** :
```
Date: Monday, 21 11 2018 21:14:34 GMT
```
5. "**I don't trust users who can be tracked.**", set the value of the `DNT` Header to **1**:
```
DNT: 1
```
6. "**This website is only for people from Sweden.**", for this one we will use `X-Forwarded-For` to spoof our IP address, I pinged `amazon.se` and grabbed its IP address, you can grab any other swedish one.
```
X-Forwarded-For: 52.94.223.26
```
7. "**You're in Sweden but you don't speak Swedish?**", makes sense.. let's simply change the language tag in the `Accept-Language` **Header** to the swedish one `sv`

            Accept-Language: sv

![[Flag]](https://github.com/Redhawk1EE7/Redhawk1EE7.github.io/blob/main/_posts/_img/picoCTF/who-are-you/3.png?raw=true "flag")

# Bonus!