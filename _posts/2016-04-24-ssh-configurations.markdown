---
layout: post
title:  "SSH configurations"
date:   2016-04-23 10:21:54 +0530
categories: ssh devops
---

---
Now a days, am using ssh command a lot and learnt few things on the way. Thought of noting down the configurations which are useful.

Before that,

`ssh-keygen -t rsa -b 4096 -C "mymailid@gmail.com" -f tmp`

This is the command to generate the private & public key pair combo, out of which you ll share the public key to the remote machine for authentication. Private key should be used from local machine to login to the remote machine.

###authorized keys

	Go to the remote machine which you want to ssh into and create this file `~/.ssh/authorized_keys`. Now copy the generated public key into it. And after that you can login to that machine using,

	 `ssh -i ~/.ssh/tmp remotemachine.com`

	Another simpler way is to use `ssh-copy-id`. But in mac, you have to install this. I used brew `brew install ssh-copy-id` and to execute this command, you have to use password based authentication.

Command :

 `ssh-copy-id -i ~/.ssh/tmp test@somemachine.com`

  This will copy the public key to `somemachine`'s authorized_keys file and you can use the `tmp` private key to login to the machine.

###ssh config

	Another way to login to frequently used machine is to create a file `.ssh/config` and copy the below information,

	```
Host my-machine
           Hostname somemachine.com
           User test
           IdentitiesOnly yes
           IdentityFile ~/.ssh/somemachine
	```
Now you can simply use,

		ssh my-machine

This will login as user `test` into `somemachine`

---
