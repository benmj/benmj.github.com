Date: 2012-08-21
Title: Scripting Permission Changes for Pelican
Tags: personal, code, bash, geeky
Author: Ben Jacobs

I'm not a frequent blogger. To date, this is my second blog post. But this doesn't mean that I don't enjoy toying around with different blogging and publishing software. Last week, I decided to move my Wordpress blog to the static blogging software [Pelican](http://www.getpelican.com). After looking around at the guts of Wordpress, I was turned off by its complexity. I also really really really wanted to be able to edit posts offline and in my own [editor](http://www.sublimetext.com).

Pelican comes with a pretty robust Makefile that can recompile and upload your website via SSH. I ran into a small issue with my Godaddy account, in which all new files and folders were unreadable because of permission issues. The files needed to be readable by all users on the server and the folders needed to be executable by all users. I wrote a little bash script called **permissions.sh** and uploaded it to my server.

	#!/bin/bash
	# permissions.sh

	find ./ -type d | xargs chmod a+x
	chmod -R a+r *

The new "trick" for me was the **find -type d** to only list directories. I then added the following line to my Pelican Makefile under the **ssh_upload** section:

	ssh $(SSH_USER)@$(SSH_HOST) ./permissions.sh

Works great! <s>The only issue is that I have to type my twice, once for the SCP transfer and once for the SSH command. I'll look around and see if there are any ways to store these credentials for a tiny moment in time. If not, typing the password twice is a small price to pay for not having to remotely log into the server every time I make a change.</s>

As soon as I uploaded the last paragraph (dutifully entering my password twice), I decided to search around for a way to authenticate the connection between my computer and the server without the passwords. I found [this little jewel](http://www.linuxproblem.org/art_9.html) and it works even better. Vive le unix.