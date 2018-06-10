# STUDENT PORTAL - VNIT

INTRODUCTION
------------

An Automate webportal which generates the notices and sends to respective client, whre he/she will be provided the charge sheet and is required to pay the fine online.


SETUP
-----

* First of all (if it's not) install python 2.7 in your machine.
```
$ brew install python #for UNIX
```
* You'll get the basic steps to install it on internet easily according to your configuration. (It's recommended to use LINUX/UNIX configurations, but you can find similar steps for windows also.)

* This is recommended to install pycharm ide to contribute in this project (https://www.jetbrains.com/pycharm/)

* After installing the ide, we need to install our project and its dependencies but before that it's a good practice to create virtual environment using ```virtualenv```
* ```virtualenv``` is a tool to create isolated Python environments. Refer it's documentation to know [more.](https://virtualenv.pypa.io/en/stable/ "more.")

INSTALL
--------
* Now Let's Install Virtualenv with pip
*There are other ways also to install virtualenv but I prefer this.*

```sh
$ easy_install pip
```
* Next step is to install the virtualenv package: 

```sh
$ pip install virtualenv
```

 Great you have installed ```virtualenv```on your machine.

* Create an Environment with virtualenv
Before creating the environment, let's seperate our project files. Let's create one directory.
```sh
$ mkdir mydirectory && cd mydirectory
```
 To create the environment with virtualenv:
```sh
$ virtualenv python portalenv  #see alternative if you are using other than LINUX/UNIX.
```
 After creating virtual environment, it's time to activate it. Type this command
```sh
$ source portalenv/bin/activate
```

 Now, we are all set to clone out project from github and open it on pycharm.

* Cloning the project

 Type this command in terminal to clone the repo.
```sh
$ git clone https://github.com/sagban/stupo-task.git
```
 To check wether the cloning process done corectly type ``` ls```,and it'll look like this.
```sh
ls
portalenv stupo-task
``` 


   *Note: The directory 'mydirectory' is only to seperate the things from your stuff, so it won't effect out project because all the project stuff is in the repo we just cloned. So, don't try to rename it.*
  
  Since, we've just cloned our project it's time to open it in a super powerfull IDE pycharm
 * Now, open the project in pycharm.(directory stupo-task)
 * Setting up the interpreter for out project.
   In tab bar, go to File > Settings or Default Settings > Project Interpreter.
   now, create new local interpreter with using base interpreter python2.7 and existing environment that we created earlier "portalvenv".
    
    Now, open the terminal in pycharm itself and it must be looklike this
    ```sh
    (portalenv) SagBans-Mac:stupo-task sagban$ 
    ```
    If it's not, then try to activate the virual environment from here by using the previous command 
    ```$ source ../portalenv/bin/activate    #be carefull of paths. This command is when you are in stupo-task repo```
    
    If everything worked fine >>
    Congratulations, you setup the StudentPortal project in your pc.
    
    


* Now it's a time to install the dependencies and devDependencies to start the development.

```sh
$ pip install -r requirements.txt
```

### Development

Installed? Great!
So, this should be your project structure
```sh
myproject/
  	stupo-task/
		portalapp/
		static/
		studentportal/
		templates/
		manage.py
		requirements.txt
  portalenv/
```
### Database
It's time to install mySQL database on your machine. Refer this great [article ]

<h3 id="mysql">MySQL</h3>

<p>If you want to use MySQL, the following <code>apt</code> commands will get you the packages you need:</p>
<pre class="code-pre "><code langs="">sudo apt-get update
sudo apt-get install python-pip python-dev mysql-server libmysqlclient-dev
</code></pre>
<p>You will be asked to select and confirm a password for the administrative MySQL account.</p>

<p>After the installation, you can create the database directory structure by typing:</p>
<pre class="code-pre "><code langs="">sudo mysql_install_db
</code></pre>
<p>You can then run through a simple security script by running:</p>
<pre class="code-pre "><code langs="">sudo mysql_secure_installation
</code></pre>
<p>You'll be asked for the administrative password you set for MySQL during installation.  Afterwards, you'll be asked a series of questions.  Besides the first question which asks you to choose another administrative password, select yes for each question.</p>

<p>With the installation and initial database configuration out of the way, we can move on to create our database and database user.  Skip ahead to the next section.</p>


<div name="create-a-database-and-database-user" data-unique="create-a-database-and-database-user"></div><h2 id="create-a-database-and-database-user">Create a Database and Database User</h2>

<p>The remainder of this guide can be followed as-is regardless of whether you installed MySQL or MariaDB.</p>

<p>We can start by logging into an interactive session with our database software by typing the following (the command is the same regardless of which database software you are using):</p>
<pre class="code-pre "><code langs="">mysql -u root -p
</code></pre>
<p>You will be prompted for the administrative password you selected during installation.  Afterwards, you will be given a prompt.</p>

<p>First, we will create a database for our Django project.  Each project should have its own isolated database for security reasons.  We will call our database <code><span class="highlight">myproject</span></code> in this guide, but it's always better to select something more descriptive.  We'll set the default type for the database to UTF-8, which is what Django expects:</p>
<pre class="code-pre "><code langs="">CREATE DATABASE <span class="highlight">myproject</span> CHARACTER SET UTF8;
</code></pre>
<p>Remember to end all commands at an SQL prompt with a semicolon.</p>

<p>Next, we will create a database user which we will use to connect to and interact with the database.  Set the password to something strong and secure:</p>
<pre class="code-pre "><code langs="">CREATE USER <span class="highlight">myprojectuser</span>@localhost IDENTIFIED BY '<span class="highlight">password</span>';
</code></pre>
<p>Now, all we need to do is give our database user access rights to the database we created:</p>
<pre class="code-pre "><code langs="">GRANT ALL PRIVILEGES ON <span class="highlight">myproject</span>.* TO <span class="highlight">myprojectuser</span>@localhost;
</code></pre>
<p>Flush the changes so that they will be available during the current session:</p>
<pre class="code-pre "><code langs="">FLUSH PRIVILEGES;
</code></pre>
<p>Exit the SQL prompt to get back to your regular shell session:</p>
<pre class="code-pre "><code langs="">exit
</code></pre>
<div name="install-django-within-a-virtual-environment" data-unique="install-django-within-a-virtual-environment"></div><h2 id="install-django-within-a-virtual-environment">Install Django within a Virtual Environment</h2>

<p>Now that our database is set up, we can install Django.  For better flexibility, we will install Django and all of its dependencies within a Python virtual environment.</p>

<p>You can get the <code>virtualenv</code> package that allows you to create these environments by typing:</p>
<pre class="code-pre "><code langs="">sudo pip install virtualenv
</code></pre>
<p>Make a directory to hold your Django project.  Move into the directory afterwards:</p>
<pre class="code-pre "><code langs="">mkdir ~/<span class="highlight">myproject</span>
cd ~/<span class="highlight">myproject</span>
</code></pre>
<p>We can create a virtual environment to store our Django project's Python requirements by typing:</p>
<pre class="code-pre "><code langs="">virtualenv <span class="highlight">myprojectenv</span>
</code></pre>
<p>This will install a local copy of Python and <code>pip</code> into a directory called <code><span class="highlight">myprojectenv</span></code> within your project directory.</p>

<p>Before we install applications within the virtual environment, we need to activate it. You can do so by typing:</p>
<pre class="code-pre "><code langs="">source <span class="highlight">myprojectenv</span>/bin/activate
</code></pre>
<p>Your prompt will change to indicate that you are now operating within the virtual environment. It will look something like this <code>(<span class="highlight">myprojectenv</span>)<span class="highlight">user</span>@<span class="highlight">host</span>:~/<span class="highlight">myproject</span>$</code>.</p>

<p>Once your virtual environment is active, you can install Django with <code>pip</code>.  We will also install the <code>mysqlclient</code> package that will allow us to use the database we configured:</p>
<pre class="code-pre "><code langs="">pip install django mysqlclient
</code></pre>
<p>We can now start a Django project within our <code>myproject</code> directory.  This will create a child directory of the same name to hold the code itself, and will create a management script within the current directory.  Make sure to add the dot at the end of the command so that this is set up correctly:</p>
<pre class="code-pre "><code langs="">django-admin.py startproject <span class="highlight">myproject</span> .
</code></pre>
<div name="configure-the-django-database-settings" data-unique="configure-the-django-database-settings"></div><h2 id="configure-the-django-database-settings">Configure the Django Database Settings</h2>

<p>Now that we have a project, we need to configure it to use the database we created.</p>

<p>Open the main Django project settings file located within the child project directory:</p>
<pre class="code-pre "><code langs="">nano ~/<span class="highlight">myproject</span>/<span class="highlight">myproject</span>/settings.py

<p>This is currently configured to use SQLite as a database.  We need to change this so that our MySQL database is used instead.</p>

<p>First, change the engine so that it points to the <code>mysql</code> backend instead of the <code>sqlite3</code> backend.  For the <code>NAME</code>, use the name of your database (<code><span class="highlight">myproject</span></code> in our example).  We also need to add login credentials.  We need the username, password, and host to connect to.  We'll add and leave blank the port option so that the default is selected:</p>
<pre class="code-pre "><code langs="">. . .

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.<span class="highlight">mysql</span>',
        'NAME': '<span class="highlight">myproject</span>',
        'USER': '<span class="highlight">myprojectuser</span>',
        'PASSWORD': '<span class="highlight">password</span>',
        'HOST': 'localhost',
        'PORT': '',
    }
}

. . .
</code></pre>

<div name="migrate-the-database-and-test-your-project" data-unique="migrate-the-database-and-test-your-project"></div><h2 id="migrate-the-database-and-test-your-project">Migrate the Database and Test your Project</h2>

<p>Now that the Django settings are configured, we can migrate our data structures to our database and test out the server.</p>

<p>We can begin by creating and applying migrations to our database.  Since we don't have any actual data yet, this will simply set up the initial database structure:</p>
<pre class="code-pre "><code langs="">cd ~/<span class="highlight">myproject</span>
python manage.py makemigrations
python manage.py migrate
</code></pre>
<p>After creating the database structure, we can create an administrative account by typing:</p>
<pre class="code-pre "><code langs="">python manage.py createsuperuser
</code></pre>
<p>You will be asked to select a username, provide an email address, and choose and confirm a password for the account.</p>

<p>Once you have an admin account set up, you can test that your database is performing correctly by starting up the Django development server:</p>
<pre class="code-pre "><code langs="">python manage.py runserver</code></pre>
<p>In your web browser, visit your server's domain name or IP address followed by <code>:8000</code> to reach default Django root page:</p>
<pre class="code-pre "><code langs="">http://<span class="highlight">127.0.0.1</span>:8000
</code></pre>
<p>You should see the default index page:</p>

<p><img src="https://assets.digitalocean.com/articles/django_mysql_1404/django_index.png" alt="Django index"></p>

<p>Append /admin to the end of the URL and you should be able to access the login screen to the admin interface:</p>

<p><img src="https://assets.digitalocean.com/articles/django_mysql_1404/admin_login.png" alt="Django admin login"></p>

<p>Enter the username and password you just created using the <code>createsuperuser</code> command.  You will then be taken to the admin interface:</p>

<p><img src="https://assets.digitalocean.com/articles/django_mysql_1404/admin_interface.png" alt="Django admin interface"></p>

<p>When you're done investigating, you can stop the development server by hitting CTRL-C in your terminal window.</p>

<p>By accessing the admin interface, we have confirmed that our database has stored our user account information and that it can be appropriately accessed.</p>

*Don't forgot to activate virtual environment in every new terminal ( WE USE MANY THESE ;) ).*


### Guidelines for Managing code

* Everyone write and push code in your respective git branches.
* And then after you can create pull request of *branch* -> *master* from the github
* No one will push directly in master branch.
*Watch tutorials on git, github and version control to learn How to work with branches*
* Make sure scripts, templates, models, url related to the particular app you creates should in their respective folder. 

MAINTAINED BY
-------------
Team StudenPortal. Check here

