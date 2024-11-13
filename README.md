
# Trading Exchange Collaborative Learning Program

This repo introduces the Trading Exchange Collaborative Learning Program from the [Prescription Free Academy of Web Development and Software Engineering](https://prescriptionfree.academy/).

It includes general information and documentation relating to the program, along with links to individual project repos.

Resources that apply to the program can go here. It’s not intended for code, but could be used in future for  scripts that relate to the program in general.

It’s the starting point if you’re looking for something.

## Contents

1. [System Architecture and General Ramble](#system-architecture-and-general-ramble)
    1. [The Client](#the-client)
    2. [Application Layer](#application-layer)
    3. [Data Access Layer](#data-access-layer)
    4. [Data Services](#data-services)
2. [Interfaces](#interfaces)
3. [Interface Agreements](#interface-agreements)
    1. [With All That Said](#with-all-that-said)
    2. [Interface Style](#interface-style)
    3. [Application Layer Interface](#application-layer-interface)
    4. [Data Access Layer Interface](#data-access-layer-interface)
    5. [Data Services Interface](#data-services-interface)
4. [Existing Implementations](#existing-implementations)
5. [Getting Started](#getting-started)
    1. [Development Tools](#development-tools)
6. [Project Ideas](#project-ideas) 
7. [Conclusion](#conclusion)

## System Architecture and General Ramble

The trading exchange is a multitiered, multi-tenant, distributed system. It is intended to have multiple clients and support new ones without modification to other layers.

That’s a lot of terms but since this is a learning project, it seems important to be proper.

At least where it’s helpful to be.

It’s a system with multiple parts. Multiple layers. And intended to have multiple options for implementation of the layers.

Primarily the client and the server. But that would be client-server architecture. And the web is always that (ok you can open a HTML file in a web browser)(that’s not client-server)(but don’t!).

This system has a bit more than that. And particularly because we’re looking to get practice working with more. But it is in the end built around the web. And we’re not looking to operate outside of that.

It’s intended as an extensive and open system, providing opportunities to practice with all aspects of software engineering for the web.

### The Client

So there’s the client. Let’s start there.

The client is whatever you want it to be. Most likely that’ll be a web application. But if you want to build a handheld device and write the client in assembly, go ahead. Just make sure it can talk HTTP, as we’re not looking to make it available through any other protocol.

(For the picky out there, yes, we’ll no doubt need to set up WebSocket at some point, but I’m waiting for a student to step up to that, and in picky response it’s essentially part of HTTP anyway.)

But I suppose you could always build a gateway to translate HTTP to whatever and back. So even that’s not beyond the bound of possibility.

Whatever those are.

But for the less adventurous of us, the client is going to be a web application.

We’re not big fans of React around here, so it’ll likely be Angular, Vue or vanilla JS.

What does the client do? Well that depends who builds it.

This is a collaborative project, so you might work alone on a small client with limited or even narrowly focused functionality (a website widget that displays tickers), or collaborate on something more substantial, or even build something more substantial yourself (such as a trading app).

As this moves forward and clients start to be developed, info will be posted to this repo.

### Application Layer

This is where a simpler system would just be “server”. One server application to do everything.

We’re going a bit further than that. So there’s an application tier that handles communication with the client. An API.

But it doesn’t handle any data. At least other than passing it through. That’s the job of the data access layer, which we’ll look at next.

It handles application logic and makes available an appropriate interface for the client.

Business logic also goes here. Although there can be some of that in the data access layer too.

It’s possible to have a separate business logic layer, but we’re not currently looking at doing that.

So the beauty of this approach is that it’s flexible how it’s hosted. You can have multiple instances of the application layer and less of the data access, if that’s what’s needed to handle the load.

You can move the application layer closer to the user and keep the data access where the data is, causing only the necessary traffic across the distance between.

You can plug and play the pieces. Making use of different implementations of the layers as desired.

It’s a well established and well used architecture. Do some research on it. Also know as N-tier architecture. (Share any useful links and other useful findings in the comments)

The beauty of this approach for us, along with getting practice working with this kind of architecture, is that you can build just one piece and then have it interact with pieces made by others.

It’s all about the interfaces, and I’ll talk more about that soon, once we get through this initial introduction to the approach to the architecture.

### Data Access Layer

The data access layer is a tier that handles all data access. It communicates with the application tier and consumes data services.

### Data Services

Data services plug in to the data access layer. Although there are interface agreements for the services, it is also possible that this can be open and individual services provided as appropriate, perhaps with a set of optional interface modules if that works.

We’re looking to experiment with service-oriented architecture as the data services in this imaginary economy of ours can be disparate and varied in purpose.

Data services can be mock data or the possibility exists for consuming real trading data for transformation and repurposing.

## Interfaces

So it’s all about the interfaces.

I said it before and I’ll no doubt say it again.

That’s how modular software works. Whether it’s a function, a class or a layer of an N-tier architecture. It needs a solid interface that isn’t tied to any implementation details. So the implementation can change without changing the interface. So it’s built to represent what the module does rather than how it does it. And so that it works in a consistent, clean and coherent way for whatever it needs to do, whatever way it needs to do it, for now, the foreseeable future, and in some cases, also the unforeseeable.

It’s an art. And one that takes practice.

And it’s achieved by keeping it simple and abstracted from implementation details.

Consider CRUD. Create, Read, Update, Delete. It can support whatever you might want to do with data. It’s abstracted. It doesn’t care what data you add, what you delete, what you change. It’s a clean, coherent and consistent surface for working with data.

That’s a simple example. But a good one. Your abstractions and interfaces will be more complex, but the principles are the same.

Google has a pretty cool [API Design Guide](https://cloud.google.com/apis/design/). It talks about “networked APIs” but the  principles are also great learning for modular software in general.

We’ll specify interfaces for the layers. We have to, so all work to the same interfaces, or the system couldn’t function.

Within the piece that you write, the interfaces will be up to you. And the principles are the same.

So look at it, discuss it, learn. And then get in to designing them yourself.

## Interface Agreements

### With All That Said…

With all that said about us needing to have agreements about the layer interfaces, it doesn’t have to be so inflexible.

It’s certainly helpful to include that in the approach. For those working on a particular piece and focusing on learning how to do that, it’s helpful to have a structure to work to.

So this is for them. And for anyone else who wants to work with this but doesn’t want to learn about or experiment with designing programming interfaces of that type.

However, for those that do, you can of course have a go at this any way that you want. What you produce doesn’t need to work with what others produce.

And if there turns up an alternative approach that works well then hey, we can look at having two sets of interfaces. Or more. It all depends who comes along and what seems fun and useful to learn.

For now, we’re focusing on coming up with an interface set that works and we can take it forward from there.

### Interface Style

All interfaces are currently HTTP network APIs set up with a REST style. A GraphQL setup is planned for the future.

Other interface styles will be considered and set up as appropriate.

### Application Layer Interface

End Points for Individual Tickers    
Potentially `GET /ticker/{TICKER_ID}`

End Point for Ticker List    
Potentially `GET /tickers`

Filters for Ticker List

- Category
- Price Range
- Ticker ID Set (default all)
- What else?

### Data Access Layer Interface

[None Yet]

### Data Services Interface

[None Yet]

## Existing Implementations

These are existing implementations of the layers. They can be put together locally to run a complete system.

Live instances will be set up in the future.

### Clients

[None yet]

### Application Layer

These are available implementations of the application layer.

Open Exchange Data    
[GitHub - pecknigel/open-exchange-data](https://github.com/pecknigel/open-exchange-data)

### Data Access Layer

These are available implementations of the data access layer.

Open Exchange Connector    
[GitHub - pecknigel/open-exchange-connector](https://github.com/pecknigel/open-exchange-connector)

### Data Services

These are available implementations of data services.

Open Exchange Tickers  
[GitHub - pecknigel/open-exchange-tickers](https://github.com/pecknigel/open-exchange-tickers)

## Getting Started

As clients are developed you’ll be able to use those to try out the system.

For now, or to try out backend layers directly, the best tool is an HTTP client such as:

Postman    
[Download Postman](https://www.postman.com/downloads/)

Using Postman you can make HTTP requests and see the responses.

We intend to put together Postman collections as things start coming together.

For information on how to get an individual project set up and running on your local computer, see the README file for the project. If there isn’t one, consider getting involved and starting by writing one or improving what’s there.

### Development Tools

You’re going to need an IDE or Integrated Development Environment. We highly recommend WebStorm from JetBrains. It’s just so much more fun and useful to use than VS Code. And now (November 2024) has a free version for non-commercial work, which all of this is classed as. The paid version is not an expensive subscription - choose “For Individual Use” if looking at pricing.

[WebStorm from JetBrains](https://www.jetbrains.com/webstorm/)

## Project Ideas

There are several ways that you can get involved with the program in order to learn and gain experience. How much involvement you have is really up to you.

At the least, you can pick up one of the projects, run it on your computer and see how it works. Everything that you need to do that is openly available. You can modify the code, connect it with other projects/layers, and work with it however you like.

If you’d like more structure and guidance to your learning then mentoring sessions are available. These can be booked as you need them via the main website [Prescription Free Academy](https://prescriptionfree.academy/).

The following ideas for clients that you could develop might be useful.

#### Trading Application

A web application for trading.

#### Website Widget

A website widget for displaying ticker prices.

#### Comprehensive Application Layer API

Design and develop a comprehensive API for handling exchange trading.

#### Crypto Data Service

Create a data service for piping real crypto price data.

#### Fake Purchases Data Service

Create a data service for generating fake trades that can be used as a basis for fake markets.

#### Event Based Data Service

A data service based on an event bus that fires off price change events and amalgamates them to a live price list. Potentially with distributed services firing events. Potentially use Observables.

#### Symbol Registry Service

Create a service for centrally managing the list of symbols, so that data services can use that as a basis for the data that they generate. Include categories and other metadata.

#### Debug Service Monitor

Create a tool for debugging that consumes one or more data services and displays their data in real time on a web interface.

#### Your Own Ideas

There are so many possibilities for practicing software development with a fake trading exchange system. See what you can come up with or discuss it with a mentor. Share and discuss your ideas in the comments.

## Conclusion

It’s all a work in progress and designed for learning and working on and practicing with - rather than all being perfect when you find it.

Stay tuned! And keep coding!
