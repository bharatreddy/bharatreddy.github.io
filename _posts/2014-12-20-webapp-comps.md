---
layout: post
title: Components for building a basic interactive webapp.
---

In this post I'll discuss the ingredients necessary for building a simple and interactive webapp. Do note that the current article is not a comprehensive tutorial for building a webapp, rather it presents a discussion to help choose a light-weight and reusable tech stack.

Before getting into choosing the tech stack and frameworks for the app, we'll need an overview of the architecture of the app. The most fundamental elements of any webapp are the backend, frontend and an interface. The backend is where we store our data and do some analysis using the data. More often than not we like to hide our backend from users (for example when the data is really valuable for us or when the analysis is a secret recipe). The frontend is where we present the results of our analysis in a meaningful way to the user. In an interactive webapp the user is provided with the capability to retreive a new set of results by changing some options provided to them (like a dropdown menu or a search bar we find in many websites). Finally, the interface part acts as a medium of communication between the frontend and the backend. Refer to [this article](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) for more details on understanding architectures employed to build user interfaces.

The current app uses MySQL and Python as the core backend of the app. The frontend is composed of bootstrap, jquery and d3.js. Flask is the webframework (interface) used. The complete code for the app is hosted on my [github account](https://github.com/bharatreddy/cricstats).

## The tech stack

- [Flask](http://flask.pocoo.org/) : A web microframework based on python. I use it for the backend of the app. Flask is a minimalistic and simple framework which is easy to learn and deploy. Flask is particularly suited for developing light-weight webapps.
- [Bootstrap](http://getbootstrap.com/) : A powerful and easy to use frontend framework developed by twitter. It includes html and css design templates for different elements of a webpage such as buttons, tables, forms and much more. With Bootstrap we can create beautiful and responsive web layouts with very little effort. Another added advantage of bootstrap is its compatibility with different browsers and devices.
- [Pandas](http://pandas.pydata.org/) : An awesome python library used for data analysis. Pandas is great when working with medium sized data sets (data which can fit in the memory of a single machine). One of the advantages of Pandas is speed which is a crucial factor when working with websites performing data analysis on the fly.
- [d3.js](http://d3js.org/) : An interactive plotting library.
- [MySQL](http://www.mysql.com/) : A relational database where we store our data.