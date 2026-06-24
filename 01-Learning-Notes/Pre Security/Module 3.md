# Module 3 – How the Web Works

## DNS in Detail

DNS stands for Domain Name System. The whole point of it is to save us from having to memorize IP addresses for every website we visit. Instead of typing something like 104.26.10.229 into a browser, we type google.com and DNS handles the translation behind the scenes.

A domain name has different parts to it. The rightmost part, like .com or .org, is called the TLD or Top-Level Domain. Generic TLDs like .com were originally meant to indicate purpose (commercial, educational, government), while country-code TLDs like .co.uk or .ca indicate geography. Over time, hundreds of new TLDs have been added.

The part just before the TLD, like "google" in google.com, is called the Second Level Domain. This is the actual name registered by whoever owns the domain.

### DNS Record Types

DNS holds different types of records depending on what's being looked up.

An A record maps a domain to an IPv4 address. An AAAA record does the same but for IPv6 addresses. A CNAME record points one domain to another domain rather than an IP, which is common when services are hosted on external platforms. MX records are specifically for email and tell mail servers where to deliver messages for a domain, with a priority order in case the main server goes down. TXT records hold free-form text data, often used to verify domain ownership or indicate which servers are authorized to send email on behalf of the domain.

### How DNS Resolution Works

When you type a domain into your browser, a series of steps happen to find the correct IP address.

First, your computer checks its own local cache to see if it already knows the answer. If not, the request goes to a Recursive DNS Server, usually provided by your ISP, which also has its own cache. If that comes up empty too, it contacts a Root DNS Server. The root server doesn't know the final answer but points the request toward the correct TLD server. The TLD server then directs the request to the Authoritative DNS Server for that specific domain, which holds the actual DNS records and returns the IP address. That answer travels back through the chain and gets cached along the way.

Every DNS record has a TTL (Time To Live) value that controls how long it stays in cache before a fresh lookup is needed.


## HTTP in Detail

HTTP (HyperText Transfer Protocol) is the set of rules that governs how your browser communicates with web servers. It was developed by Tim Berners-Lee between 1989 and 1991. When you load a webpage, everything you see, the HTML, images, videos, is transferred using HTTP.

HTTPS is the secure version of HTTP. The data is encrypted in transit, which prevents others from reading it and also confirms you are actually talking to the real server and not an imposter.

### What a URL Is

A URL (Uniform Resource Locator) is essentially the full address of a resource on the internet. It can contain several components:

The scheme tells the browser which protocol to use, such as HTTP, HTTPS or FTP. The host is the domain name or IP address of the server. The port specifies which port to connect on, usually 80 for HTTP and 443 for HTTPS. The path points to a specific file or location on the server. A query string passes extra parameters to the server, like a search term or a record ID. A fragment references a specific section within a page.

### Making a Request

A basic HTTP request looks like this:


GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/


The first line specifies the method (GET), the resource being requested (/), and the HTTP version. The following lines are headers that give the server additional context. Every HTTP request ends with a blank line to signal that the request is complete.

### HTTP Methods

HTTP methods tell the server what action the client wants to perform.

GET is used to retrieve information. POST is used to submit data, often to create a new record. PUT is used to update existing data on the server. DELETE is used to remove a record.


## HTTP Headers

Headers are extra pieces of information sent alongside HTTP requests and responses.

Common request headers include Host, which tells the server which website is being requested when multiple sites share the same server. User-Agent identifies the browser and its version. Content-Length tells the server how much data to expect in the body of the request. Accept-Encoding lists the compression formats the browser supports. Cookie sends stored data back to the server.

Common response headers include Set-Cookie, which tells the browser to store a cookie. Cache-Control specifies how long the browser should keep the response cached. Content-Type tells the browser what kind of data is in the response, such as HTML, JSON or an image. Content-Encoding indicates what compression was applied to the data.



## Cookies

Cookies exist because HTTP is stateless, meaning the server has no memory of previous requests. Every request looks brand new to the server by default.

When a server responds with a Set-Cookie header, the browser saves that data and sends it back with every future request to that domain. This is how websites remember who you are across pages or sessions. In authentication, a cookie usually stores a session token rather than your actual password, a unique value the server can match to your logged-in session.

You can inspect what cookies your browser is sending through the developer tools, under the Network tab.



## How Websites Work

When you visit a website, your browser sends a request to a web server somewhere in the world. That server processes the request and sends back the data your browser uses to render the page.

Websites are generally split into two sides. The front end is everything the browser renders and the user interacts with directly. The back end is the server-side logic that handles requests, talks to databases, and builds the response.

### HTML Injection

HTML injection is a vulnerability that happens when user input is placed directly into a page without being sanitized first. If a website takes what a user types and displays it as raw HTML, an attacker can inject their own HTML or JavaScript into the page and manipulate how it looks or behaves.

The fix is input sanitization. Before any user input is used in the page or passed to a function, the application should strip or escape any HTML tags. The general principle is to never trust user input and always validate or clean it before using it anywhere in the application.
