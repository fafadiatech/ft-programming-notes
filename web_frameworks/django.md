# Notes on Djano

## Django internals

1. [Django in Depth](https://www.youtube.com/watch?v=tkwZ1jG3XgA)
1. [Where can i get technical information on how the internals of Django works?](https://stackoverflow.com/questions/1286176/where-can-i-get-technical-information-on-how-the-internals-of-django-works)
1. [How Django processes a request](http://www.b-list.org/weblog/2006/jun/13/how-django-processes-request/)
1. [How the Heck do Django Models Work](http://lazypython.blogspot.in/2008/11/how-heck-do-django-models-work.html)
1. [Project Django - This book talks about Django internals](http://www.apress.com/us/book/9781430258094)

## Django in Depth

1. Bottom up approach, start from bottom work our way up
1. ORM
    - Down the rabbit hole {Bottom Up}:
        1. Database backend:
            - Loweset level interaction with Database
            - This is what `ENGINE` part of database settings
            - This is the bounday {beyond this its database drive module}
            - Made of few components
                - `DatabaseWrapper`: This is the basic information about database {and SQL dialect}
                    - This is where mappings from say TextField to native Datatype done
                    - This resides in `django.db.backends.base`
                - `DatabaseOperations`: Knows how to do common casts and value extraction
                - `DatabaseFeatures`: What does database supports
                - `DatabaseCreation`: Quirks of creating the database/tables
                - `DatabaseIntrospection`: Used by `inspectdb` management command
                - `DatabaseSchemaEditor`: This is how we do migrations {generate bunch of SQL ALTER statements}
                - `DatabaseClient`: This is what is used by `dbshell` management commands
        1. SQLCompiler: 
            - Turns a Django Query instance into SQL for your database
            - Subclasses for non-SELECT queries
                - SQLInsertCompiler for INSERT
                - SQLDeleteCompiler for DELETE
            - `Query.get_compiler()` return SQLCompiler
            - Which calls `compiler()` method of DatabaseOperations, passing the name of desired compiler
            - Which in-turn calls `DatabaseOperations.compiler_module`
        1. Query: These are basic datastructures and methods to high level re-presentation
                - `BasicQuery`: ORM queries
                - `RawQuery`: Bring your own queries {This is for optimizing your query}
                - Query is a tree {a tree-like datastructure}. So basically generating query is like traversing tree and generating final query. This is repeated in templates aswell. 
                - [Query expressions](https://docs.djangoproject.com/en/1.11/ref/models/expressions/)
        1. QuerySet: Basically a wrapper {instance of Query needs to be wrapped for performing operations on ti}
            - Lazy {does not, changes atrributes at most}
            - Container has resusts cache
        1. Manager: Write your own query set {this can be chained}. You can use it with creating your own QuerySet, attach it your Manager
        1. Model: This is the ORM {this uses Metaclasses}





## [Qualities of great reusable Django apps by Flávio Juvenal da Silva Junior](https://www.youtube.com/watch?v=AMg4Iind90Q)

1. Concept {For re-usable apps}:
    - Do one thing and one thing well
    - Easy to check: if you can describe what your app does in few words
1. What maps a django app great?
    - Easy to install
        - Make it available on PyPi `pip install django-something`
        - Use wheels for distribution
        - Add LINCENSE
        - Add it to `Django Packages`
        - Check if its Django vs Python Packages
            - Djang App: If it needs to be added to `INSTALLED_APPS`
            - Python: Otherwise
        - Have good defaults
        - Make sure you have right prefixed settings "DJANGO_SOMETHING_SOMETHING"
        - Friendly upgrade policy
            - Use deprecation warnings before removing
            - Use [semantic versioning](http://semver.org/)
    - Easy to use
        - Provide Documentation
            - Write docs **first** 
            - Think about problem first and comeup with simple solution
            - Provide a **quick-start** tutorial, this will cover most of the common use-cases
            - Separate high-level docs from low-level docs {Django does this}
            - Use gender neutral pronouns
        - Ship with an example project
        - Fail-fast: Raise errors if developers have forgotten to update default settings
    - Easy to integrate
        - Easy to **adapt** to project needs
        - [Designing and Evaluating Reusable Components](https://mollyrocket.com/casey/stream_0028.html)

## Blog Posts
1. [Django's Generic ListView with django_filters and django_tables2](http://www.craigderington.me/django-generic-listview-with-django-filters-and-django-tables2/)
1. [Django: List of Useful URL Patterns](https://simpleisbetterthancomplex.com/references/2016/10/10/url-patterns.html)
