The goal of the project is to create web server visible for other people
Source: tutorial.djangogirls.org/ru/django_start_project

1) add virtual environment
$ python3 -m venv myvenv
$ source myvenv/bin/activate

2) check if pip is installed
(myvenv) $ python3 -m pip install --upgrade pip

3a) create file «requirements.txt» with the list of dependencies
Django~=3.2.10

3b) install libraries
(myvenv) $ pip install -r requirements.txt

4) create template project
(myvenv) $ django-admin startproject mysite .
Here: * django-admin.py creates useful directories and files
      * manage.py helps to manage site. Also it helps to run web server on my computer
      * settings.py contains website settings

5) fix mysite/settings.py file
Add STATIC_ROOT — info about static file location
Add ALLOWED_HOSTS — because we want to run web server on pythonanywhere.com

6) create database
(myvenv) $ python3 manage.py migrate

7) run web server 
(myvenv) $ python3 manage.py runserver
Starting development server at http://127.0.0.1:8000/

###########################################################################################

8) create application
(myvenv) $ python3 manage.py startapp blog

So project structure becomes:
djangogirls
|
 - blog
|
 - db.sqlite3
|
 - manage.py
|
 - mysite

9) Say Django to use application
Add ‘blog’ to INSTALLED_APPS in mysite/settings.py

10) migrate model ‘blog’ to database
(myvenv) $ python3 manage.py makemigrations blog
returns:
Migrations for 'blog':
  blog/migrations/0001_initial.py
    - Create model Port

11) add model to database
(Myvenv) $ python3 manage.py migrate blog
Returns:
Operations to perform:
  Apply all migrations: blog
Running migrations:
  Applying blog.0001_initial... OK

#########################################################################################

12) import model Post
Add "admin.site.register(Post)" to blog/admin.py file

13) look at model Post
(myvenv) $ python3 manage.py runserver
Go to http://127.0.0.1:8000/admin/

14) create superuser
(myvenv) $ python3 manage.py createsuperuser
Username (leave blank to use 'svetlanamironova'): admin
Email address: admin@admin.com
Password: 
Password (again): 
This password is too common.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.

15) go to http://127.0.0.1:8000/admin/ as admin
Result: Django settings panel appears

16) go to Posts folder of the Django settings panel appears and add some posts

#########################################################################################
Git repo

17) initialise empty repo
(myvenv) $ git init

18) create .gitignore

19) add useful files, create commit:
git status, git add, git commit

20) create repository on GitHub, add origin
(myvenv) $ git remote add origin git@github.com:MironovaSveta/my-first-blog.git

21) push changes
(myvenv) $ git push --set-upstream origin main

#########################################################################################
Deploy

22) register at www.pythonanywhere.com

23) create API token for PythonAnywhere

24) run Bash console at PythonAnywhere:
pip3.6 install --user pythonanywhere
pa_autoconfigure_django.py https://github.com/...
python manage.py createsuperuser

  -----------------------------------
/                                     \
| All done!  Your site is now live at |
| https://blacksky.pythonanywhere.com |
\                                     /
  -----------------------------------

#########################################################################################
URLconf

In mysite/urls.py:
urlpatterns = [
    path('admin/', admin.site.urls),
]
= for each URL starting with admin/ Django will find corresponding view (= представление)

VIEW requests info from model and conveys info into template
Views are like methods in Python

25) add line for importing blog.urls (in file mysite/urls.py)

26) create blog.urls and add URL-template
    * file blog/urls.py

27) add view to blog/views.py

28) create template, in HTML = Hyper Text Markup Language
    blog/templates/blog/post_list.html

########################################################################################
Deploy-pull

29) commit changes

30) go to PythonAnywhere
cd ~/<your-pythonanywhere-domain>.pythonanywhere.com
git pull

########################################################################################
QuerySet

Is a list of objects of a model

31) open Django terminal
(myvenv) $ python3 manage.py shell
List all in blog:
  * from blog.models import Post
  * Post.objects.all()
Create new user
  * from django.contrib.auth.models import User
  * User.objects.all() # lists all users
  * user = User.objects.create_user(username='john',
...                                  email='jlennon@beatles.com',
...                                  password='glass onion')
Create post object
  * Post.objects.create(author=user, title='Sample title', text='Test')
Filter objects
  * Post.objects.filter(author=user)
  * Post.objects.filter(title__contains='title')
Publish post
  * post = Post.objects.get(title='Sample title')
    post.publish()
List published posts
  * from django.utils import timezone
    Post.objects.filter(published_date__lte=timezone.now())
Sort objects
  * Post.objects.order_by('created_date')
  * Post.objects.order_by('-created_date')
    = descending order
Join QuerySets
  * Post.objects.filter(published_date__lte=timezone.now()).order_by('created_date')
Close Django console
  * exit()

#######################################################################################
Dynamic data

32) add model to blog/views.py

33) convey list of posts to a template in blog/views.py
    blog/templates/blog/post_list.html
    * {{posts}}
    * more accurate: 
      {% for post in posts %}
        {{ post }}
      {% endfor %}

34) git-gui to push changes

35) PythonAnywhere: git pull, Web -> Reload

#######################################################################################
CSS = Cascading Style Sheets

We will use Bootstrap framework (https://getbootstrap.com/)

36) install bootstrap, so add lines to blog/templates/blog/post_list.html

37) add static file: blog/static/css/blog.css
    * h1 a = CSS selector
    * element has name (a, h1, body) and attribute class/id

38) use recently created css file
    Add line to blog/templates/blog/post_list.html