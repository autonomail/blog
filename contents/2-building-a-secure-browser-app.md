{{{
  "title": "Building a secure browser app",
  "tags": ["security", "chrome"],
  "category": "general",
  "date": "11-28-2013"
}}}

A decision we made early on was to build Autonomail using web technologies. We feel that this 
will allow us to quickly develop a user-friendly interface that works well across the myriad of different devices that 
we all like to use nowadays. The popularity of Gmail only reinforces the fact that as a whole, most people are quite 
comfortable using webmail, especially given the advantages a webmail interface has over traditional desktop-heavy 
mail apps.

However, unlike Gmail we are primarily focussed on your mail's security and privacy. And one of the problems with 
delivering code over the web is that 
if care isn't taken, it's very easy for a malicious attacker to compromise the code which comprises an app whilst it's making its way to 
your computer from the server. This is a [well known issue](http://www.matasano.com/articles/javascript-cryptography/). 
And even if everything does reach your computer in-tact and unmodified, browser security holes and other bugs may allow 
malicious code to modify the behaviour of the app once it is loaded and running.

To work around such issues Autonomail will be built as a [Chrome app](http://developer.chrome.com/apps/about_apps.html) 
_(Firefox to come later)_. A Chrome app runs within the Chrome browser environment like any other web page. But what 
differentiates it from a normal 
web page is that all the code needed to run the app can be downloaded and stored offline on your machine and then launched from there as and 
when you need it. This is much safer than downloading the code from the server everytime you wish to use it (which is how 
normal webmail works). Furthermore, Chrome apps are run in their own separate 'sandbox', isolating them from other 
web pages and web apps. They also have access to privileged features which normal web pages cannot access. This includes 
reading from and writing to the local file system, opening up network connections to other servers, etc. This 
in turn allows us to provide you a more native-app-like experience even though you will still essentially be running 
a web app.

And if we decide we can't trust the browser running the app then there are tools which 
allow us to [bundle a trusted version of the browser](https://github.com/adobe/brackets-shell) along with the app.

Thus we don't plan to offer the 
ability to access your account through our website. Given the issues we've outlined above, allowing you to login through 
the website would put your password and therefore your privacy at risk. Combining this restriction with our Chrome app 
makes it 
easier for us to avoid certain web attacks (e.g. [CSRF](http://en.wikipedia.org/wiki/Cross-site_request_forgery)). It also 
forces us to build our server back-end with a purely service-oriented architecture. That simply means we can make it 
easier to test and integrate with other software, thereby providing you with a better experience.

In future posts we will delve deeper in to the architecture Autonomail app, including how we plan to keep your password 
and other data safe from prying eyes.
