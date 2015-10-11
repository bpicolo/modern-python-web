---
layout: post
title:  "Writing Your First Route"
date:   2015-10-10 20:46:08
categories: webdevelopment
---
The first thing we're going to want to do is install the <a href="http://flask.pocoo.org/">flask</a> package.
Flask is a simple to use python web framework that gives us all the tools to do
more or less whatever we want. Because of this, we'll be able to dig a
bit deeper into how exactly web applications work.

<figure class="terminal code">
<figcaption>terminal</figcaption>
{% highlight shell-session %}
pip install flask
{% endhighlight %}
</figure>

After that, we can create a file (in our case app.py) to put the web server
startup script in.

<figure class="code">
<figcaption>app.py</figcaption>
{% highlight python3 %}
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
    return 'Hello World'

if __name__ == '__main__':
    app.run(port=5000)
{% endhighlight %}
</figure>

So, lets walk our first piece of app code. The first thing we do is
import the flask app constructor (simple enough) and create an instance
of Flask called <ic>app</ic>.<br>

We then define a new route for the app. Flask uses a decorator, signified
by <ic>@</ic>, to denote a route. A Python decorator is fancy way
to write a function which accepts another function as an argument.
In our case, the <ic>@app.route</ic> decorator itself takes one argument: the url that
this route is for. <br>

The last part of code has two components. <ic>if __name__ == '__main__':</ic>
lets us only run the next portion of code if we're calling this file as a script from the command line,
as Python will set the __name__ variable for us. (Conversely, this block
of code will not be called if we import this file from another python file).
All that's left to do after that is run the app, which starts a simple
web server using our routes.


<figure class="terminal code">
<figcaption>terminal</figcaption>
{% highlight shell-session %}
bash - $ python app.py
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
{% endhighlight %}
</figure>

<row>
    <p>
    At this point, our website is up and running (available to us only and not
    the rest of the world). Open your browser and navigate to the URL
    given when we run the app, in our case <ic>http://127.0.0.1:5000/</ic>.
    In it, you should see your route's output:
    </p>

    <div class="twelve columns">
    <img class="u-max-full-width" src="/assets/1-1.png"></img>
    </div>
</row>

