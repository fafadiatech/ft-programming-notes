# Notes on Djano

## Django internals

1. [Where can i get technical information on how the internals of Django works?](https://stackoverflow.com/questions/1286176/where-can-i-get-technical-information-on-how-the-internals-of-django-works)
1. [How Django processes a request](http://www.b-list.org/weblog/2006/jun/13/how-django-processes-request/)
1. [How the Heck do Django Models Work](http://lazypython.blogspot.in/2008/11/how-heck-do-django-models-work.html)
1. [Project Django - This book talks about Django internals](http://www.apress.com/us/book/9781430258094)

## [Qualities of great reusable Django apps by Flávio Juvenal da Silva Junior]

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
        - 