## Django Url Mapping
### What is a URL?

 * A URL is a web address. You can see a URL every time you visit a website – it is visible in your browser's address bar.(Yes!     127.0.0.1:8000 is a URL! And localhost:8000 is also a URL! And https://github.com/ is also a URL! )
 <img src="images/url.png" alt="url image"/>
 
 * Every page on the Internet needs its own URL. This way your application knows what it should show to a user.In Django, we use something called URL configuration.URL configuration is a set of patterns that Django will try to match the requested URL to find the correct view.

------------------------------------------

### Creating a Django Project & Application!
#### django installation
* Whether you are on Windows or Linux, just get a terminal or a cmd prompt,then use this code −

```
    pip install django
           (or)
    pip install django == 2.2.7
 ```
* After installing Django, you need to create a project  using django


#### Create a Project
* Whether you are on Windows or Linux, just get a terminal or a cmd prompt and navigate to the place you want your project to be created, then use this code −

````
$ django-admin startproject myproject
````


* Next, create an application using manage.py

#### Create an Application
* We assume you are in your project folder. In our main “myproject” folder, the same folder then manage.py −

````
$ python manage.py startapp myapp
````

#### Get the Project to Know About Your Application
* At this stage we have our "myapp" application, now we need to register it with our Django project "myproject". To do so, update INSTALLED_APPS tuple in the settings.py file of your project (add your app name) −

````
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',
]
````


------------------------------------------

 ### How do URLs work in Django?
  * Let's open up the myproject/urls.py file in your code editor like SublimeTool and see what it looks like:
  <img src="images/urlsconf.png" alt="urlconf image"/>
  
  * As you can see, Django has already put something here for us.
  * We have only one url in myproject/urls.py that is **The admin URL** and that is for admin stuff.
  
   
 ------------------------------------------
 ### Types of URLs?
 #### We have 2 types Urls:
    1. Static Urls 
    2. Dynamic Urls
             
  ------------------------------------------
 ### Your first Django URL!
 * We can add our first URL pattern:
     * In myproject/urls.py for creating url we will use path function
     * In myproject/urls.py ,we have to import views from myapp, for that add this line in urls.py
  ````   
  from myapp import views
  ```` 
  * It looks like(myproject/urls.py):
   <img src="images/importviews.png" alt="importviews image"/>
   
   ------------------------------------------
   
  ### Configuring the Static URL:
  **`In Urls.py:`adding Static msg url path**
  * for that path we will give different values like:
  
         path('urlname/',views.funtionname,name='nameoftheurl'),
  * example:
  ````
            path('msg/',views.msg,name='msg'),
   ````
  * It looks like(myproject/urls.py):

   <img src="images/msg.png" alt="msg image"/>
   
   **`In views.py: importing HttpResponse and adding msg function`**
   * In views.py, we have to import HttpResponse, for that add this line in views.py
   
           
            from django.http import HttpResponse
            
   * In views.py we have add a function, with name we used in urls.py that is **msg**
   
   ```
               def msg(request):
                   return HttpResponse('<h2>Welcome to all <br> This is ur Static Url</h2>')
   ```
   
   > NOTE: In this function, request is a default parameter,we can't change that.
   
   * It looks like(myapp/views.py):
   <img src="images/defmsg.png" alt="defmsg image"/>
   
   **Run Project:**
   
   * save the changes  and start server using **python manage.py runserver**
   *  Then open chrome:
   
    localhost:8000/url
   * example:
      
             localhost:8000/msg
             
   **OutPut for Static Url:**
   * Then we get OUTPUT it looks like:
   <img src="images/msgop.png" alt="msgop image"/>

 ------------------------------------------
### Configuring the Dynamic URL:

### `for string:`

  **`In Urls.py:adding Dynamic string hello url path`**
  * for that path we will give different values like:
  
         path('urlname/<str:name>',views.funtionname,name='nameoftheurl'),
  * example:
  ````
            path('hello/<str:name>',views.hello,name='hello'),
   ````
  * It looks like(myproject/urls.py):

   <img src="images/hello.png" alt="hello image"/>
   
   **`In views.py: importing HttpResponse and adding hello function`**
   * In views.py, we have to import HttpResponse, for that add this line in views.py
   
           
            from django.http import HttpResponse
            
   * In views.py we have add a function, with name we used in urls.py that is **hello**
   
   ```
               def hello(request,name):
                   return HttpResponse(<center><h2>Hi '+name+'<br>Welcome to Dynamic String Url</h2></center>)
   ```
   
   > NOTE: In this function, request is a default parameter,we can't change that.
   
   >  NOTE: Remember that in url what u taken as string name, that only passed in this function as a second parameter,it's better                to maintain samename in urls and views(inside function) also.     
        
   
   * It looks like(myapp/views.py):
   <img src="images/defstrhello.png" alt="defstrhello.png"/>
   
   **Run Project:**
   
   * save the changes  and start server using **python manage.py runserver**
   *  Then open chrome:
   
    localhost:8000/url/name
   * example:
      
             localhost:8000/hello/Apssdc
             
   **OutPut for Dynamic String Url:**
   * Then we get OUTPUT it looks like:
   <img src="images/helloop.png" alt="helloop.png"/>

---------------------------------------
### `for Integer:`

  **`In Urls.py:adding Dynamic integer rollno url path`**
  * for that path we will give different values like:
  
         path('urlname/<int:id>',views.funtionname,name='nameoftheurl'),
  * example:
  ````
            path('rollno/<int:id>',views.rollno,name='rollno'),
   ````
  * It looks like(myproject/urls.py):

   <img src="images/hellorollno.png" alt="hellorollno image"/>
   
   **`In views.py: importing HttpResponse and adding rollno function`**
   * In views.py, we have to import HttpResponse, for that add this line in views.py
   
           
            from django.http import HttpResponse
            
   * In views.py we have add a function, with name we used in urls.py that is **rollno**
   
   ```
               def rollno(request,id):
                   return HttpResponse(<center><h2>Hello {} <br>Welcome to Dynamic Integer Url</h2></center>'.format(id))
   ```
   
   > NOTE:  Remember that in url what u taken as string name, that only passed in this function as a second parameter,it's better to            maintain samename in urls and views(inside function) also. 
    
   > NOTE: In this function, request is a default parameter,we can't change that.
   
   * It looks like(myapp/views.py):
     <img src="images/defintrollno.png" alt="defintrollno image"/>
   
   **Run Project:**
   
   * save the changes  and start server using **python manage.py runserver**
   *  Then open chrome:
   
    localhost:8000/url/id
   * example:
      
             localhost:8000/rollno/528
             
   **OutPut for Dynamic integer Url:**
   * Then we get OUTPUT it looks like:
   <img src="images/rollnoop.png" alt="rollnoop.png"/>

---------------------------------------
  ### `for multiple values:`

  **`In Urls.py:Adding Dynamic multiple values like name, id,mobile url path`**
  * for that path we will give different values like:
  
         path('urlname/<str:name>/<int:id>/<int:mobile>',views.funtionname,name='nameoftheurl'),
  * example:
  ````
            path('studata/<str:name>/<int:id>/<int:mobile>',views.studata,name='studata'),
   ````
  * It looks like(myproject/urls.py):

   <img src="images/multipleurls.png" alt="multipleurls image"/>
   
   **`In views.py: importing HttpResponse and adding studata function`**
   * In views.py, we have to import HttpResponse, for that add this line in views.py
   
           
            from django.http import HttpResponse
            
   * In views.py we have add a function, with name we used in urls.py that is **studata**
   
   ```
               def studata(request,name,id,mobile):
                   return HttpResponse(<h2>Hello {} <br>Your rollno:{}<br>Your Mobileno:{}</h2>'.format(name,id,mobile))
   ```
   
   > NOTE:  Remember that in url what u taken as string name, that only passed in this function as a second parameter,it's better to            maintain samename in urls and views(inside function) also. 
    
   > NOTE: In this function, request is a default parameter,we can't change that.
   
   * It looks like(myapp/views.py):
     <img src="images/multipleviews.png" alt="multipleviews image"/>
   
   **Run Project:**
   
   * save the changes  and start server using **python manage.py runserver**
   *  Then open chrome:
   
    localhost:8000/url/name/id/mobile
   * example:
      
             localhost:8000/apssdc/528/8887665767
             
   **OutPut for Dynamic integer Url:**
   * Then we get OUTPUT it looks like:
   <img src="images/multipleop.png" alt="multipleop.png"/>

-------------------------------------------

 ### `Configuring Another app Urls :`
 #### Create an Application
* We assume you are in your project folder. In our main “myproject” folder, the same folder then manage.py −

````
$ python manage.py startapp myapp2
````
**`In settings.py:`**
#### Get the Project to Know About Your Application
* At this stage we have our "myapp2" application, now we need to register it with our Django project "myproject". To do so, update INSTALLED_APPS tuple in the settings.py file of your project (add your app name) −

````
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',
    'myapp2',
]
````
------------------------------------------
  **`In myproject/urls.py:`**
  * For adding urls in different app first we have to add **include** in mainurls.py and include myapp2 urls in mainurls.py:
  * for that path we will give different values like:
    
         from django.urls import path,include
        
         path('myapp2/',include('myapp2.urls')),
  
  * It looks like(myproject/urls.py):

   <img src="images/anotherappmainurl.png" alt="anotherappmainurl image"/>
   
   **After including myapp2 urls in myproject/urls.py then in myapp2 we have to create one file,with the name urls.py.**
   * It looks like(myapp2/urls.py):

   <img src="images/anotherapp.png" alt="anotherapp image"/>
   
   **`In myapp2/urls.py:`**
  * In myapp2/urls.py ,we have to import views from myapp, for that add this line in myapp2/urls.py.
                                
                                from django.urls import path
                                from myapp2 import views

  * In myapp2/urls.py for creating url we will use path function:

          urlpatterns=[
                path(‘data/<str:name>/<int:id>’,views.data,name=’data’),
            ]
  
  * It looks like(myproject/urls.py):

   <img src="images/anotherappurl.png" alt="anotherappurl image"/>
   
   **`In views.py: importing HttpResponse and adding msg function`**
   * In views.py, we have to import HttpResponse, for that add this line in views.py
   
           
            from django.http import HttpResponse
            
   * In views.py we have add a function, with name we used in urls.py that is **data**
   
   ```
               def data(request,name,id):
                   return HttpResponse('<h2>Hello {}<br>ur rollno: {}</h2>'.format(name,id))
   ```
   
   > NOTE: In this function, request is a default parameter,we can't change that.
   
   * It looks like(myapp/views.py):
   <img src="images/anotherappviews.png" alt="anotherappviews image"/>
   
   **Run Project:**
   
   * save the changes  and start server using **python manage.py runserver**
   *  Then open chrome:
   
    localhost:8000/myapp2/data/name/id
   * example:
      
             localhost:8000/myapp2/data/stateskilldevelopment/401
             
   **OutPut:**
   * Then we get OUTPUT it looks like:
   <img src="images/anotherappop.png" alt="anotherappop image"/>

 ------------------------------------------








