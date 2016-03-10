---
layout: post
title:  "File Permission and Creator s personality"
<!-- date:   2015-12-25 09:21:54 +0530 -->
categories: random unix
---

Just a random thought about file permission and what type of personality is the creator of the file is,

| sno 	| mode| personality 	 	     |
|:------|-----|--------------------------|
|1  	|700  | selfish-git.json         |
|2  	|070  | patriot-saint-like.json  |
|3  	|007  | saint-god-like.json      |


To set the context :

In the file permission mode eg: 764,

first digit represents `owners permission` - 7,
second digit represents `groups permission` - 6,
third digit represents `others permission` - 4

also,

	1 - execute permission
	2 - write permission
	4 - read permission

so 764 can be written as

(1 + 2 + 4) (2 + 4) (4) - which implies,

	all permission for the creator of file,
	read and write permission for the group in which file belongs to,
	read permission for others.
