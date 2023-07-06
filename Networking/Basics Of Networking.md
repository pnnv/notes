#### IP Address and basic Networking
It is just a way through which other computers know who you are, and based off of a complicated routing system. 

To find out IP Address we can run `ip addr`. This will print out a list of things called interface and some other stuff. IP addresses of the form `127.0.0.1` are known as **IPV4** addresses. (There's another format known as IPV6).

`127.0.0.1` is called our local host, aka, out computer's local IP address.

#### Routing
```bash
$ traceroute google.com
```

This shows a printout of all the hosts we are hopping across, starting with our gateway router and ending with google.com server. This family of commands is useful for troubleshooting networking problems.

Our local IP address is completely different from our public IP this is because of something called **NAT** or Network Address Translation which is a method of mapping one IP address to another by modifying packets while they are in transit.
- In simple terms, our local IP is stored by some NAT server which ensures that any responses to traffic from us that leave our network, come back to out locally assigned IP. On the other hand, nobody should be able to connect into a box behind NAT because they will not know the local IP address and either way, a local address shouldn't be routed across the internet.
- Basically, NAT allows connections out and responses back, but does not allow connections in.

#### VM Networking
Virtualisation software gives an option to switch your VM between a NAT'd IP address and a Bridged IP address.

- Bridged IP addresses are IP addresses assigned by your local router, which will be NAT'd by the router when you try to connect out. NAT'd IP addresses are IP addresses assigned by out virtualisation software, which puts that box behind a NAT.
- This means that if we are NAT'd, other computers can't connect to us directly, but if we are bridged, our IP address will be routable.



##### Clients and Servers
Computers connected to the internet are called clients and servers.
- Clients are typical web user's internet-connected devices (for example our computer is connected to Wi-Fi or phone is connected to mobile data) and web-accessing software like firefox or chrome.
- Servers are computers that store webpages, sites, or apps. When a client device wants to access a webpage, a copy of the webpage is downloaded from the server onto the machine to be displayed in the user's web browser.

- **Internet connection**: Allows us to send and receive data on the web
- **TCP/IP**: Transmission Control Protocol and Internet Protocol are communication protocols that define how data should travel across the internet .
- **DNS**: Domain Name System is like an address book for websites. When we type a web address in out browser, the browser looks at the DNS to find thr website's IP address before it can retrieve the website.
- **HTTP**: Hypertext Transfer Protocol is an application protocol that defines a language for clients and servers to speak to each other.
- **Component Files**: A website is made up of different files, which are like different parts of the goods  you buy from the shop. These files come in two types:
	- **Code Files**: Websites are primarily built from HTML, CSS, ans JavaScript.
	- **Assets**: This is the collective name for all the other stuff that makes up a website, such as images, video, word documents and PDFs.
[More on this](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works)


1. The browser goes to the DNS server, and finds the real address of the server that the website lives on.
2. The browser sends an HTTP request message to the server, asking it to send a copy of the website to the client. The website and all the other data is sent to us using TCP/IP.
3. The server approves client's request, the server sends the client a "200 OK" message, which means "Of course you can look at the website! Here it is", and then starts sending the website's files to the browser as a series of small chunks called data packets.
4. The browser assembles all the small chunks into a complete web page and displays