# Flask-Blogging

Flask is a small and lightweight Python web framework that provides useful tools and features that make creating web applications in Python easier. It gives developers flexibility and is a more accessible framework for new developers since you can build a web application quickly using only a single Python file. Flask is also extensible and doesn’t force a particular directory structure or require complicated boilerplate code before getting started.

Flask uses the Jinja template engine to dynamically build HTML pages using variables, loops, lists, and so on. 

In this, we'll be leveraging Flask and SQLite in Python 3. Users of the application can view all the posts in our database and click on the title of a post to view its contents with the ability to add a new blog post and edit or delete an existing post

### Setting up the database

We'll be setting up database to store blog post for application. We'll be using SQLite database file to store your data because the sqlite3 module, which we will use to interact with the database, is readily available in the standard Python library.

First, because data in SQLite is stored in tables and columns, and since your data mainly consists of blog posts, you first need to create a table called posts with the necessary columns. You’ll create a .sql file that contains SQL commands to create the posts table with a few columns. You’ll then use this file to create the database.

The schema.sql inside directory, content explained below:

The first SQL command is `DROP TABLE IF EXISTS` posts;, this deletes any already existing tables named posts so you don’t get confusing behavior. Note that this will delete all of the content you have in the database whenever you use these SQL commands. Next, `CREATE TABLE` posts is used to create the posts table with the following columns:

`id`: An integer that represents a primary key, this will get assigned a unique value by the database for each entry (that is a blog post).
`created`: The time the blog post was created at. NOT NULL signifies that this column should not be empty and the DEFAULT value is the CURRENT_TIMESTAMP value, which is the time at which the post was added to the database. Just like id, you don’t need to specify a value for this column, as it will be automatically filled in.
`title`: The post title.
`content`: The post content.

## Running your application 

Firstly, install flask in your machine
`$ pip3 install flask` 

Once installed run `python -c "import flask; print(flask.__version__)"` to validate if the installation is success or not. 

To validate if the flask server is up and running you can try below snippet (small hello flask code):

```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, from Flask!'
    
if __name__ == "__main__":
    app.run(debug=True)
```

In the init_db.py we are importing sqlite3 module and then opening a connection to db file, which will be created by running 
`python3 init_db.py`

If this run is success you will see that a new database.db file will appear in your main directory. If you see something like this means you are on track to setup your application. 

`$ python3 app.py`

```
'FLASK_ENV' is deprecated and will not be used in Flask 2.3. Use 'FLASK_DEBUG' instead.
 * Serving Flask app 'app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://127.0.0.1:5000
Press CTRL+C to quit
 * Restarting with stat
'FLASK_ENV' is deprecated and will not be used in Flask 2.3. Use 'FLASK_DEBUG' instead.
 * Debugger is active!
 * Debugger PIN: 116-444-089
 ```

You will see output as above. 

Once you browse it you will see below page: 

<img width="1379" alt="image" src="https://user-images.githubusercontent.com/25319514/191034084-4daab4ed-b602-4545-b29a-1a3ce7a615ba.png">
