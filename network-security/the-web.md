# The Web

The Internet is one of those things that everyone uses, but few people bother to learn about. As hackers, it is vital that we understand what exactly the web is, and how it works.

When you open up your web browser and navigate to a website, it seems so simple, but what is really happening behind the scenes?

First of all, your computer communicates with a known DNS \(**D**omain **N**ame **S**ystem\) server to find out where the website can be found on the internet. The DNS server will then return an **IP address** for the remote server. This can be used to go directly to the website. You can think of the internet as being quite like the planet itself -- we have lots of locations, all over the world. These places all have a street address -- this is akin to the domain name of a website \(i.e. tryhackme.com, or google.com\); but they also have co-ordinates which can be used to pinpoint their location with absolute accuracy. These co-ordinates are like the IP address of a website. If you know the street address of a location, you can enter it into Google Maps and be given the exact coordinates, which can then be put into a SatNav to take you there with pinpoint accuracy!

In the same way, your browser is given the address of a website \(i.e. tryhackme.com\). It sends this address off to a DNS server, which tells it the "co-ordinates" \(the IP address\) of the site. Your computer doesn't understand the original, human-readable domain name, but it _does_ understand what an IP address is! The IP can then be used to find the server across the internet, allowing your computer to request the content of the website. Of course, in reality, this is a highly simplified analogy, so a more in-depth explanation of this process can be found [here](https://tryhackme.com/room/introtonetworking).

### HTTP\(S\):

Once your computer knows where it can find the target website, it sends something called a HTTP \(**H**yper**t**ext **T**ransfer **P**rotocol\) request to the webserver.

This is just a standard network request, but it is formatted in a way that both your web browser and the server can understand. In practice, this means adding certain "headers" to the request which identify it as a HTTP request, and tell the server a variety of other information about the request, as well as your own browser. Amongst many other headers, HTTP requests always have a _method_ and a _target_. These specify _what_ to retrieve from the server \(the target\), and _how_ to retrieve it \(the method\). The method most commonly used to _retrieve_ information is called the GET method. When sending data _to_ the server, it's more common to use a method called POST.

For more information about HTTP requests, methods and headers, check out the [Web Fundamentals](https://tryhackme.com/room/webfundamentals) room!

Once the content has been retrieved from the server, your browser reads the retrieved code and renders it as a web page. This usually means taking the layout of the page from a HTML \(**H**yper **T**ext **M**arkup **L**anguage\) document, styling it with a connected CSS \(**C**ascading **S**tyle **S**heets\) file, then adding any dynamic content with one or more connected JavaScript files.

HTTP has one inherent disadvantage: namely, it is not secure. Anyone can see what you're requesting, and what's being sent back to you. For this reason, HTTPS \(**H**yper**t**ext **T**ransfer **P**rotocol **S**ecure\) was invented. This works in exactly the same way as standard HTTP but provides an encrypted connection \(the functionality of which is beyond the level of this dossier\)

### Cookies:

HTTP is an inherently _stateless_ protocol. This means that no data persists between connections; your computer could make two requests immediately after each other, and, without relying on separate software, the web server would have no way to know that it was you making both the requests. This begs the important question: if HTTP is stateless, then how do login systems work? The web server must have a way to identify that you have the right level of access, and it can hardly ask you to enter your password every time you request a new page!

The answer is cookies -- tiny little pieces of information that get stored on your computer and get sent to the server along with every request that you make. Authentication \(or session\) cookies are used to identify you \(these will be _very_ important in your mission today!\). The server receives your request with the attached cookie, and checks the cookie to see what level of access you are allowed to have. It then returns a response appropriate to that level of access.

For example, a standard user should be able to see \(but not interact with\) our control panel; but Santa should be able to access everything! Cookies are also often used for other purposes such as advertising and storing user preferences \(light/dark theme, for example\); however, this will not be important in your task today. Any site can set cookies with a variety of properties -- the most important of these for today's task are the name and value of the cookies, both of which will always be set. It's worth noting that a site can only access cookies that are associated with its own domain \(i.e. google.com can't access any cookies stored by tryhackme.com, and vice versa\).

It's important to note that cookies are stored locally on _your_ computer. This means that they are under your control -- i.e. you can add, edit, or delete them as you wish. There are a few ways to do this, however, it's most commonly done by using your Browser Developer Tools, which can be accessed in most browsers by pressing `F12`, or `Ctrl + Shift + I`. With the developer tools open, navigate to the `Storage` tab in FireFox, or the `Application` tab in Chrome/Edge and select the `Cookies` menu on the left hand side of the console.

![](https://i.imgur.com/0moCyoO.png)

In the above image you can see a test cookie for a website. The important attributes "Name" and "Value" are shown. The name of a cookie is used to identify it to the server. The value of the cookie is the data stored by the server. In this example the server would be looking for a cookie called "Cookie Name". It would then retrieve the value "CookieValue" from this cookie.

These values can be edited by double-clicking on them, which is great if you can edit a session or authorization cookie, as this can lead to an escalation of privileges, assuming you have access to an Administrator's authorization cookie.

## Resources

[https://tryhackme.com/room/adventofcyber2](https://tryhackme.com/room/adventofcyber2)

