Date: 2012-10-03
Title: A Better Bucket
Tags: code
Author: Ben Jacobs

## Or: a fantastic journey of exploration and discovery

#### Or: A Single-Post blog entry platform

The other day, I was thinking about the gulf in ways to publish content to the web. On the one hand, there's Twitter or Facebook. These both offer easy, yet ephemeral ways, to share content. Facebook has its "notes," but these are ugly and don't seem to be used very much (at least in my circles). At the other extreme, there are blogs. Anyone can set one up, and with all the free templates that are available, it's pretty easy for the average user to come up with something decent looking. The problem with blogs is that unless you're actively cultivating them, they can get stale pretty quickly. I've run across numerous blogs that have a post or two that are years old and then just drop off (I've seen this called "blog rot"). I've also seen people create blogs for the express purpose of posting one or two things. Back in the glorious days of Google Buzz, I had a friend create a blog so he could write one long post that felt too cramped on our feed. What is someone to do if they want write something, quickly publish it, and distribute the link?

Those in the coder/hacker community are probably familiar with [PasteBucket](http://www.pastebucket.com/) and other similar services. These can be used to quickly publish snippets of computer code, and they're mostly used for sharing more than would be appropriate in a forumn or IRC channel. These sites are great for this purpose, but they had some downfalls:

1. They're geared exclusively toward computer code
2. They're rather ugly
3. Oh yeah... they have ads.

While discussing my single-post blog idea online the other day, [@carljm](https://twitter.com/carljm) turned me on to [Gist.io](http://gist.io/). This is a visually attractive project that lets one take a MarkDown file stored on [Github](http://www.github.com) and render it to an HTML page. The author, Idan Gazit, also has a lovely description of why quick-and-dirty publishing services like this are useful:

> Sometimes, we just want to share a bit of writing that is neither. Maybe we want to write for a specific audience, but don’t want to address the people who usually read our blogs. Maybe it’s just something that doesn’t fit into 140 characters.

> For these situations, even setting up a Tumblr seems like too much effort. Pastebins are great, but the reading experience sucks in general, and particularly on mobile devices.

This seems like a cool service, but, even though it's aethetics are better than PasteBucket et al., it still has a hacker focus. Who else uses Github? 

So, I decided to write something. When I started to think about it, I realized this was about the simplest web-app project imaginable for a variety of reasons:

1. I wanted to keep it anonymous, so I didn't need to worry about any account information. In fact, I didn't want to cache ANY user informat
2. Open-source libraries already existed for quck and dirty text/MarkDown editors
3. Open-source libraries already existed for makeing quick and attractive pages

So, I set about the task.

## Project's Philosophy:

1. Fast
2. Elegant (aesthetically, although also internally)
3. Easy for anyone
4. Anonymous (because who the hell needs *another* online account)

## Process Process Process

It had been a little while since I'd coded a web app, and there were some things that I'd been meaning to try out: notabely the [Twitter Bootstrap](http://twitter.github.com/bootstrap/) and [NodeJS](nodejs.org). 

The last time I wrote a web app, it needed to interact with a database on a server different than the webserver. So, I naturally set about using this architecture (w/o thinking too much). I whipped up some front-end scripts for posting and querying via jQuery AJAX calls. It worked. It was ugly.

Then, I ran across [ExpressJS](http://expressjs.com/). Ah! A lovely system. I re-worked my app to serve static .html pages in almost all instances and to rely on some of the light-weight templating that comes with Express when it couldn't.

The result is a good first start, and I'm rather proud of it. An experienced developer would probably smirk at how long it took me to get some of this *very* basic stuff up and running, but I keep telling myself that I've only been messing with Bootstrap/Node/Express for a few days.

## Can I see it?

I'm afraid I haven't deployed it yet. If you want to try it for yourself, you'll have to download it and run it. If you have command line acces and already have Node installed, you can do the following:

    git clone https://github.com/benmj/betterpaste.git
    cd betterpaste
    npm install
    node app.js

The server will start running on your computer at port 3000. In the near future, I hope to find a place where I can deploy this. I was hoping Heroku would let me, but I see that they discourage relying upon the filesystem for storage. I might look into a light-weight, NoSQL, solution. If you have any recommendations, let me know.
