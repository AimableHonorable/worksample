# LEARN RAILS
## INTRODUCTION
Rails is a web application development framework written in the Ruby programming language. It is designed to make programming web applications easier by making assumptions about what every developer needs to get started. It allows you to write less code while accomplishing more than many other languages and frameworks. Experienced Rails developers also report that it makes web application development more fun.

Before learning rails we recommend to first learn web technology basics. You need to have basic knowledge about HTML, CSS, Javascript as every web developer must, you also need to have ruby programming knowledge. It is also important to have knowledge about linux commands because rails is linux based framework.

If you don't have those skills so far, read more about them and we'll see you later:
* [Web technology basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web)
* [Linux commands](https://www.guru99.com/linux-commands-cheat-sheet.html)
* [Ruby basics](https://www.ruby-lang.org/en/documentation/quickstart/)

## RAILS INSTALLATION
Before installing rails on your computer you must have ruby installed first.
open your terminal and write the following command to check whether you have ruby installed.

```
ruby -v
```
if you don't have ruby installed on your computer let's [install ruby](https://www.ruby-lang.org/en/documentation/installation/).
If ruby is installed then let's move to rails installation. **NB:This installation is for linux operating system!**
### Install node.js
Ruby on Rails requires a JavaScript runtime to compile the Rails asset pipeline. And for the Rails development on Ubuntu Linux, it's best to install and using Nodejs as the Javascript runtime.
Add the nodejs nodesource repository to the system.
```
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
```
if you don't have curl installed on your system you will face an error so install it and go back to the above command

install curl:
```
sudo snap install curl
```
Install the latest version nodejs and some additional packages using the apt command below.
```
sudo apt install -y nodejs
sudo apt install gcc g++ make
```
At this step you have nodejs installed on your computer check version by the following command
```
node -v
```
### Configure gem
RubyGems is a Ruby Package Manager, coming with the gem command-line tool. It's automatically installed when we install Ruby on the system. Update gem to the latest version and check it.
```
gem update --system
gem -v
```

### Install rails
In this tutorial, we will be using the latest stable Ruby on Rails 6.0.3.4. We will install Rails using the gem ruby package manager.
Run the following command
```
gem install rails -v 6.0.3.4
```
After the installation is complete, check the rails version.
```
rails -v
```

### Setup PostgreSQL Database for Rails Development
By default, Ruby on Rails is using the SQLite database. It supports many databases system, including MySQL, SQLite, and PostgreSQL. And for this guide, we will be using PostgreSQL.Advertisement
Install the PostgreSQL database using the apt command below.
```
sudo apt install postgresql postgresql-contrib libpq-dev -y
```
After all installation is complete, start the Postgres service and enable it to launch everytime at system boot.
```
systemctl start postgresql
systemctl enable postgresql
```
Next, we will configure a password for the Postgres user, and create a new user for the Rails installation.
Login to the 'postgres' user and run the Postgres shell.
```
su - postgres
psql
```
Change the Postgres password using the query below.
```
\password postgres
```
Type your password and the password for postgres user has been added.

Now we will create a new role for our rails installation. We will create a new role named 'rails_dev' with the privilege of creating the database and with the password 'aqwe123' (you may use your password that you can easily remember).
Run the Postgres query below.
```
create role rails_dev with createdb login password 'aqwe123';
```
Now check all available roles on the system.
```
\du
```
Result should be like this

![postgres](https://github.com/AimableHonorable/worksample/blob/master/images/postgres.png)

After you see that the role is created, then type `\q` and `exit`
## RAILS FIRST APPLICATION
### Create rails application
Move to the directory where you want to install your rails application and then create our first rails app named 'first_app' with default database 'postgreSQL' by the following command
```
mkdir rails_apps
cd rails_apps
rails new first_app -d postgresql
```
### Run rails application
After application creation a folder named first_app will be created. Now you can change the directory to application directory
```
cd first_app
```
Create a database for your application
```
rails create:db
```
Then run your application by starting the server.
```
rails s
```
when server started open your browser and type
```
localhost:3000
```
When you see the output like below, Congratulations :clap: :clap: :clap: your application is running, now you can start using it!

![welcome](https://github.com/AimableHonorable/worksample/blob/master/images/welcome.png)

Make sure rails and ruby versions displayed match the versions you have on your computer

### Rails console
The console command lets you interact with your Rails application from the command line. On the underside, rails console uses IRB, so if you've ever used it, you'll be right at home. This is useful for testing out quick ideas with code and changing data server-side without touching the website.
Type the following command to start using console
```
rails c
```
If you wish to test out some code without changing any data, you can do that by invoking
```
rails console --sandbox.
```
Inside the rails console you have access to the **app** and **helper** instances.
With the **app** method you can access named route helpers, as well as do requests.
```
>> app.root_path
=> "/"

>> app.get _
Started GET "/" for 127.0.0.1 at 2014-06-19 10:41:57 -0300
...
```
With the **helper** method it is possible to access Rails and your application's helpers.

```
>> helper.time_ago_in_words 30.days.ago
=> "about 1 month"

>> helper.my_custom_helper
=> "my custom helper"
```

### Rails scaffolding

Scaffolding is the easiest way to generate
While you're developing Rails applications, especially those which are mainly providing you with a simple interface to data in a database, it can often be useful to use the scaffold method.

Scaffolding provides more than cheap demo thrills. Here are some benefits −
  *  You can quickly get code in front of your users for feedback.
  *  You are motivated by faster success.
  *  You can learn how Rails works by looking at the generated code.
  *  You can use scaffolding as a foundation to jump start your development.
  
Let's create scaffold for blog and we will explain about the generated codes after in the other chapter.
```
rails generate scaffold post title:string content:text
```
### Rails migration
Migrations are a convenient way to alter your database schema over time in a consistent and easy way. They use a Ruby DSL so that you don't have to write SQL by hand, allowing your schema and changes to be database independent.

run **db:migrate**  to create the table.
```
rails db:migrate
```
After a successful migration you can open your browser and Type 
```
localhost:3000/posts
```
There you can create new post, edit, view post information  and delete the created post.

### Rails routes
The Rails router recognizes URLs and dispatches them to a controller's action, or to a Rack application. It can also generate paths and URLs, avoiding the need to hardcode strings in your views.

To see routes which your application is using, you simply Type:
```
rails routes
```
and there you can see what names you can use in your coding.

To add new routes you can use route.rb file that is in `config/routes.rb`

### MVC
MVC is a pattern for the architecture of a software application. It separates an application into the following components:

  * **Models** for handling data and business logic
  * **Controllers** for handling the user interface and application
  * **Views** for handling graphical user interface objects and presentation
Below is the figure which illustrates MVC architecture

![mvc](https://github.com/AimableHonorable/worksample/blob/master/images/mvc.png)


Text developed by [Twiringiyimana Aimable](https://github.com/AimableHonorable)

## References
* https://www.tutorialspoint.com/ruby-on-rails/rails-scaffolding.htm
* https://www.guru99.com/linux-commands-cheat-sheet.html
* https://www.howtoforge.com/tutorial/how-to-install-ruby-on-rails-on-ubuntu-1804-lts/
* https://guides.rubyonrails.org/routing.html
* https://www.sitepoint.com/model-view-controller-mvc-architecture-rails/

