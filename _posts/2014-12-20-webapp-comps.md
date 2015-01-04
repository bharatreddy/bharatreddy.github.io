---
layout: post
title: Components for building an interactive webapp.
---

In this post I'll discuss the ingredients necessary for building a simple and interactive webapp. Note that the current article is not a comprehensive tutorial for building a webapp, rather it presents a discussion to help choose a light-weight and reusable tech stack.

Before getting into choosing the tech stack and frameworks for the app, we'll need an overview of the architecture of the app. The most fundamental elements of any webapp are the backend, frontend and the interface. The backend is where we store our data and/or do some analysis. More often than not the backend is not accesible to the users (for example when the data is really valuable for us or when the analysis is a secret recipe). The frontend is where we present the results of our analysis in a meaningful way to the user. In an interactive webapp the user is provided with the capability to retreive a new set of results by changing some options provided to them (like a dropdown menu or a search bar we find in many websites). Finally, the interface part acts as a medium of communication between the frontend and the backend. Refer to [this article](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) for more details on understanding architectures employed to build user interfaces.

The current app uses MySQL, Python and Pandas as the backend. The frontend is composed of bootstrap, jquery and d3.js. Flask is the webframework (interface) used. The complete code for the app is hosted on my [github account](https://github.com/bharatreddy/cricstats).

## The tech stack

- [Flask](http://flask.pocoo.org/) : A web microframework based on python. Flask is a minimalistic and simple framework which is easy to learn and deploy. Flask is well suited for developing light-weight webapps. Furthermore, Flask is equipped with extensions which can be installed based on our requirement to perform more complicated tasks. For example, if we are building an app which needs to work with different users, requiring the functionality of registering users, checking the validity of the account (passwords, emails etc), working with user sessions and so on. We can use the [Flask-Security](https://pythonhosted.org/Flask-Security/) extension.
- [Bootstrap](http://getbootstrap.com/) : A powerful and easy to use frontend framework developed by twitter. It includes html and css design templates for different elements of a webpage such as buttons, tables, forms and much more. With Bootstrap we can create beautiful and responsive web layouts with very little effort. Another added advantage of bootstrap is its compatibility with different browsers and devices.
- [d3.js](http://d3js.org/) : A javascript based plotting library for making some really beautiful visualizations using our data. 
- [jQuery](http://jquery.com/) : A javascript library used to simplify functionality like navigating a document, working with [DOM](http://en.wikipedia.org/wiki/Document_Object_Model), creating animations, and develop [Ajax programs](http://en.wikipedia.org/wiki/Ajax_(programming)).
- [Python](https://www.python.org/) : A powerful and widely used scripting language. Here we use it in the backend.
- [Pandas](http://pandas.pydata.org/) : An awesome python library used for data analysis. Pandas is great when working with medium sized data sets (data which can fit in the memory of a single machine). One of the advantages of Pandas is speed which is a crucial factor when working with websites performing data analysis on the fly.
- [MySQL](http://www.mysql.com/) : A relational database where we store our data. However, depending on the application (especially if the data is unstructured) [MongoDB](http://www.mongodb.org) is another popular choice.

## Process outline

- Install flask (pip install Flask) and other required libraries. In case you don't already use the pip/easy_install package mangers for python, I definetly recommend doing so.
- Any Flask app has two main subfolders - static, templates. The static folder has files related to the frontend operations (through http), basically the javascript and css files. The templates folder is the place where we have the [Jinja2 templates](http://jinja.pocoo.org/docs/dev/) - the files rendered by the flask app (for example index_cric.html file in the current project).
- Get the Bootstrap files from [here](http://getbootstrap.com/getting-started/#download). There are multiple formats available for download such as the Compiled Bootstrap and Bootstrap source. I'm using the compiled version for ease of use. Also, there are plenty of free bootstrap themes available [online](http://www.blacktie.co/).
- The downloaded (and unzipped) folder should have 3 directories - css, js and fonts. The css and js folders contain the compiled/minified css and javascript bootstrap files respectively. The files in the fonts folder contain about 200 icons from the Glyphicon Halflings set.
- Place the bootstrap files in the static folder. In the templates folder create an html file named index.html.
- Change all the css and js file links in the index.html file to point to the static folder.
- A sample index.html file using boostrap is shown below. 
{% highlight html %}
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>Test bootstrap template</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- Bootstrap core CSS -->
    <link href="static/bootstrap/css/bootstrap.css" rel="stylesheet">

    <!-- Custom styles for this template -->
    <link href="static/bootstrap/css/starter-template.css" rel="stylesheet">
    <script src="static/jquery-1.10.2.min.js"></script>
    <script src="http://code.jquery.com/jquery.min.js"></script>
    <script src="js/bootstrap.min.js"></script>
</head>
<body>
  <div class="container">
    <div class="starter-template">
      <h1>Tester App</h1>
      <p class="lead" id='printUsers'>Base template</p>
    </div>
  </div>
</body>
</html>
{% endhighlight %} 
- Now we have an html page. We now need a mapper to map the html file (index.html) to othe Flask framework. Create a file called run.py in the root folder and create a mapper for the index.html file as shown below.
{% highlight python %}
from flask import Flask, render_template, request, jsonify
app = Flask(__name__)
@app.route("/")
def starter():
    return render_template('index.html')
{% endhighlight %}    
- Refer the [project page](https://github.com/bharatreddy/cricstats) for a lot of additional functionality such as using data from MySQL to make d3.js visualizations.