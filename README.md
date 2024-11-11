
# Trading Exchange Collaborative Learning Program

This repo is an umbrella for the Trading Exchange Collaborative Learning Program from Prescription Free.

It includes general information and documentation related to the program, along with links to the individual repos.

Resources can go here that apply to the program in general. It’s not intended for code, but could be used for some general scripts in the future.

It’s the starting point if you’re looking for something.

## System Architecture and General Ramble

The trading exchange is a multitiered, multi-tenant, distributed system. It is intended to have multiple clients and support new ones without modification to other layers.

That’s a lot of terms but since this is a learning project, it seems important to be proper.

At least where it’s helpful to be.

It’s a system with multiple parts. Multiple layers. And multiple options for implementation of those layers.

Primarily the client and the server. But that would be client-server architecture. And the web is always that (ok you can open a HTML file in a web browser)(that’s not client-server)(but don’t!).

This system has a bit more than that. And particularly because we’re looking to get practice working with more. But it is in the end built around the web. And we’re not looking to operate outside of that.

### The Client

So there’s the client. Let’s start there.

The client is whatever you want it to be. Most likely that’ll be a web application. But if you want to build a handheld device and write the client in assembly, go ahead. Just make sure it can talk HTTP, as we’re not looking to make it available through any other protocol.

But I suppose you could always build a gateway to translate HTTP to whatever and back. So even that’s not beyond the bound of possibility.

Whatever those are.

But for the less adventurous of us, the client is going to be a web application.

We’re not fans of React around here, so it’ll likely be Angular, Vue or vanilla JS.

What does the client do? Well that depends who builds it.

This is a collaborative project, so you might work alone on a small client with limited or even narrowly focused functionality (a widget that displays tickers), or collaborate on something more substantial, or even build something more substantial yourself (such as a trading app).

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

It’s a well established and well used architecture. Do some research on it. Also know as N-tier architecture.

### Data Access Layer

The data access layer is a tier that handles all data access. It communicates with the application tier and manages the data.

—-

[More Coming - Actively Writing November 11 2024]
