---
title: "What the heck is a RESTful API, anyways?"
description: "If I were to take myself back to the days when I first started diving into the world of development, I remember being baffled by the term RESTful and as far as I was concerned, API was just a URL…"
date: "2019-04-13T18:18:28.343Z"
categories: 
  - API
  - Restful
  - Restful Api
  - Backend
  - Development

published: true
canonicalLink: https://medium.com/@matthew.dodi/what-the-heck-is-a-restful-api-anyways-a0564b737fb3
---

![photo by [Angelina Kichukova](https://unsplash.com/@anynieel) on [Unsplash](https://unsplash.com/)](./asset-1.jpeg)

If I were to take myself back to the days when I first started diving into the world of development, I remember being baffled by the term _RESTful_ and as far as I was concerned, _API_ was just a URL that I would use in my JavaScript application in order to fetch some data from an external resource.

After a while I started wondering how that data was actually being delivered to me. It wasn’t making a lot of sense because usually URLs would just take me to a website, but the _API_ URLs would actually give me an object (a JSON object, to be exact).

So then I decided to put my thinking hat on and start the research. Below, are all the essential information I’ve gathered and learned about _RESTful API_s.

#### The Web

It’s important to understand the way the web works when it comes to understanding, designing and building APIs. In its most fundamental form, the internet is just made up of requests. For example, as a user you’d make a request to a server. This might be for a web page, an API, a JavaScript file, an image, etc. The request itself is made up of three pieces, a **verb**, which is _what you want to do_, the **headers**, which include additional information, and then the actual **content**. In the case of a simple request for a web page, the content might actually be missing.

#### GET

The most common of these requests is GET. _Hey server, I want you to give me something that you have._ This request is used retrieve a resource from a server. You can think about a GET as _hey server, please give me this webpage_ or _hey server, please give me this image_ and so on.

#### POST

POST adds a new resource. So POST says _hey server, go create me a new one of these_. With this request we usually also provide some data that’s related to the new object that we wish to create on the server.

#### PUT

The PUT verb updates an existing resource. So essentially it says _here’s the data that I may have retrieved from you earlier with some changes, please update the what’s currently on there, with these new changes, kind server_.

#### PATCH

PATCH is something that’s not as commonly used, and while it’s kind of similar to PUT, the main difference between them is in the way that the server processes the enclosed entity-data to modify the resource. In the PUT request, the data we’re sending to the server, as far as the server is concerned, might be completely different than what the previous resource was, while a PATCH requests contains a set of instruction describing how the resource that is currently residing on the server should be modified to produce a new version. Also, another difference is that when you want to update a resource with a PUT request, you have to send the full payload as the request, whereas with PATCH you only send the parameters which you want to update.

#### DELETE

And lastly, DELETE which does exactly what the name suggests, it deletes a specific resource on the server.

There are actually more HTTP request methods than the ones listed here, but these are the most common. For a full list of all the HTTP request methods that goes more in depth in to what each of them does, [click here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods).

_That’s all fine and all, but I still have no idea what the heck is a RESTful API!_

I hear ya, but if you’ve been reading up to this point, then you’ve pretty much got all the basics down. REST is nothing more than _standards._

#### REST

REST stands for **RE**presentational **S**tate **T**ransfer and it’s basically an architectural style for providing certain standards (or constraints, depending on how you see it) in the communication between computer systems on the web. When a system or an API is compliant to these standards, we call that a RESTful API.

Some of these standards are:

**Client-server architecture**. _Separation of concerns,_ I’m sure we’ve all heard that before. In this case, we’re referring to the decoupling of the user interface from the server, the separation of the client data from the server data which improves the portability of components.

**Statelessness**. All the requests and client-server communication is stateless, meaning that no client data will be stored on the server and all of the session state is stored on the client

**Cacheability**. The client should be able to cache requests (similar to how the browsers caches static elements, such as images, of a web page) in order to improve performance

**Uniform Interface**. Probably the most fundamental _REST_ standard, saying that all requests should use a _URI_ or Unique Resource Identifier.

When we’re talking about _REST_, we’re usually referring to _URI_s  that needs to be pointing at a resource. So when a user, the client, wishes to access something on our web page, the _API_ should be designed in such a way that it provides a unique address that leads to that resource. Let’s assume an example of a very simple website _(https://example.com)_ with two pages, a home page and a profile page. Usually homepages can either be accessed by appending an _/index.html_ at the end of the _URL_, or a lot of the time we can even ignore that and just access it with just _https://example.com_. And this is where I ask you to create your own _URL_ for accessing the profile page. Go ahead, I’ll give you a minute to think about how you’d want it to look like. Done? Alright. This is what mine would look like _https://example.com/profile_. If what you thought of is anything close to mine, then congratulations, you just formed your first _URI_. _/profile_, _/home_, _/users_, /cart, those are all _URI_s, they’re paths that lead to certain content on our web page. _URI_s should also be **self-descriptive**, so that if we’re consuming an _API_ and come across a _URI_ that looks like _/api/users_ or _/api/cart_ we should instantly know what data to expect from each of those.

_Do I have to follow all these standards when I’m designing an API?_

Yes, and no. When designing your _API_ you can chose to follow all of the _REST_ standards or maybe you can just follow some of them. But in the case where you to chose to follow only some of them, would your _API_ be considered _RESTful_?  Or _partially RESTful_?  Here’s where the _Richardson Maturity Model_ comes in. According to the _Richardson Maturity Model_, any _API_ can be assigned into one of the following maturity levels.

#### LEVEL 0: The Swamp of POX

At this level _API_s are not considered at all _RESTful,_ and in the communication between the server and the client there is only one address, there is no concept of _URI_s and no proper use of the HTTP Protocol, everything is defined by XML and in the case of _SOAP_ web services that is called POX (Plain Old XML).

#### LEVEL 1: Resource Based Address/URI

The very starting level of _RESTful_ _API_s. It’s concept, as I previously discussed, is based upon having unique addresses-paths that lead to different resources on the server unlike the previous level where we only had a single _URI_.

#### LEVEL 2: HTTP Protocol

This where the HTTP verbs comes in. In comparison to _API_s on level 0, that have no usage of VERBS, and level 1, that only make use of the GET or POST verbs, _API_s on this level should be using all of the HTTP verbs (PUT, DELETE, PATCH etc.)

#### LEVEL 3: HATEOAS

HATEOAS stands for Hypermedia As The Engine Of State and _API_s on this level are considered to be fully _RESTful API_s. A level 3 _RESTful API has_ multiple unique, self-descriptive _URI_s, makes use of HTTP verbs and the response includes hypermedia links that provides additional information to the user or developer who’s consuming that _API_.

_Wait, what do you mean?_

Here, let me give you an example. Let’s assume we have the following endpoint : _https://example.com/customers/5_

Sending a GET request to that _URL_ would give us back the data that’s associated of the customer that has the id 5. A level 2 mature _API_ would give us back the following response :

```
{
    "firstName": "John", 
    "lastName": "Doe", 
    "age": "25"
}
```

But in the case of a level 3 _API_ we’d receive a response along these lines :

```
{
    "firstName": "John", 
    "lastName": "Doe", 
    "age": "25", 
    "links" : [ 
        {
            "rel": "self",
            "href": "https://example.com/customer/5",
            "method": "PUT" 
        },
        {
            "rel": "self",
            "href": "https://example.com/customer/5",
            "method": "DELETE" 
        },
        {
            "rel": "orders",
            "href": "https://example.com/customer/5/orders",
            "method": "GET" 
        }
    ]
}
```

As you can see, while the data that‘s related to the customer may not have changed, we’ve also received a list of (hypermedia) links that pretty much tells us everything we need to know about the _API_ without us having to go through the documentation to find all the possible capabilities of it.

Before I end, I’d like to let you know about one last thing that I forgot to mention earlier. _URI_s often contain (optional) parameters that you can pass with the endpoint in order to influence the response (affect the number of results that will be retrieved, sort order, type of response etc.). There are four types of parameters :

**Header parameters**, which are included inside the header of the request. Usually these refer to authentication, and while I know that I didn’t get to touch on what _headers_ are_,_ since that subject can get pretty low-level, maybe in the future I will dedicate a whole article about headers and authentication.

**Path parameters**, are included in the path and are used when we’re requesting something _specific_ on the server. These parameters are _not_ optional and are usually a part of the _URI._ We used one earlier when we were requesting data specifically for the user with the id of 5 (_https://example.com/customer/5)._

**Query String parameters**, which are also included in the path of the request but _are_ optional and if present, they get appended at the end of the _URI_ after a question mark (_?_). If there are multiple query strings, they are chained together with an ampersand (_&_). The order of the query strings does not matter. An example would be _https://example.com/customers?blocked=true&results=20_ and that should give us a list of all the customers that are blocked _and_ results should be limited to a maximum of twenty.

And last but not least, **Request Body parameters** which are included in the body of the request, usually in a JSON format and are frequently used with POST requests.

Personally, I wouldn’t stress or worry too much about trying include all those standards when you’re first starting to create _API_s, what’s important is to communicate clearly, to the developers who are consuming your _API,_ what it’s capabilities are, even if that means being a little more pragmatic about it and not checking off everything from that list.

![Illustration by [Geek&Poke](http://geek-and-poke.com/)](./asset-2.png)

If you’re reading this then that means that you stuck with me all the way ‘till the end, that’s awesome! Thank you for taking the time to read through all that, it took me quite some time to put everything together and I really do hope this post helps people understand _RESTful API_s, even a little, better. Happy coding, everybody!