
# Trading Exchange Collaborative Learning Program

This repo introduces the Trading Exchange Collaborative Learning Program from the [Prescription Free Academy of Web Development and Software Engineering](https://prescriptionfree.academy/).

It includes general information and documentation relating to the program, along with links to individual project repos.

Resources that apply to the program can go here. It’s not intended for code, but could be used in future for  scripts that relate to the program in general.

It’s the starting point if you’re looking for something.

## Contents

1. [Getting Started](#getting-started)
    1. [Development Tools](#development-tools)
2. [Existing Implementations](#existing-implementations)
3. [Project Ideas](#project-ideas)
4. [Conclusion](#conclusion)

## Getting Started

As clients are developed you’ll be able to use those to try out the system.

For now, or to work with backend layers directly, the best tool is an HTTP client such as:

Postman    
[Download Postman](https://www.postman.com/downloads/)

Using Postman you can make HTTP requests and see the responses.

We intend to put together Postman collections as things start coming together.

For information on how to get an individual project set up and running on your local computer, see the README file for the project. If there isn’t one, consider getting involved and starting by writing one or improving what’s there.

### Development Tools

You’re going to need an IDE or Integrated Development Environment. We highly recommend WebStorm from JetBrains. It’s just so much more fun and useful to use than VS Code. And now (November 2024) has a free version for non-commercial work, which all of this is classed as. The paid version is not an expensive subscription - choose “For Individual Use” if looking at pricing.

[WebStorm from JetBrains](https://www.jetbrains.com/webstorm/)    
The JavaScript and TypeScript IDE

## Existing Implementations

These are existing implementations of the layers. They can be put together locally to run a complete system.

Live instances will be set up in the future.

### Clients

These are available client implementations.

Open Exchange Website Widget    
[GitHub - pecknigel/open-exchange-website-widget](https://github.com/Prescription-Free-Academy/open-exchange-website-widget)

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
