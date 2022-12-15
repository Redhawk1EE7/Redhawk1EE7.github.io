---
layout: post
title: Who are you?
date: 2022-12-14 18:40:00 -500
categories: [Writeups, picoCTF, Web]
tags: [web, writeup, easy]
---

# Overview
> Author: MADSTACKS 
## Challenge Description
> Let me in. Let me iiiiiiinnnnnnnnnnnnnnnnnnnn 
## Challenge Hints
>1. It ain't much, but it's an RFC https://tools.ietf.org/html/rfc2616
## Challenge Page
![[Challenge Page]](https://github.com/Redhawk1EE7/Redhawk1EE7.github.io/blob/main/_posts/_img/picoCTF/who-are-you/1.png?raw=true "Challenge Page")
___________
# Walkthrough
## Starting Point
After looking around the source code, the best thing we can start from is the hint provided for us: "Only people who use the official PicoBrowser are allowed on this site!".
Thus we will go immediatly to fire Burp Suite & play around with the HTTP Headers.
> I'll consider that you have already set up your Burp, if not I suggest that you check one of the available guide on the internet, it is highly recommended to have Burp Suite by your side when doing Web stuff.. 
## 


