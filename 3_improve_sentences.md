## Create new application
### Choose a rails version to use
We know that to create a new rails application we use **rails new** command

Example:
```
rails new first_app -d postgresql
```
When you have multiple versions of rails on your computer, you can specify one rails version to use while creating the application.

Assume you have both rails (6.0.3.4, 6.0.0.0), and you need to use rails (6.0.0.0). All you have to do is to add the version after rails.

Example:
```
rails _6.0.0.0_ new first_app -d postgresql
```
### Change rails version for an existing project
For an existing version you can change the version of rails in **Gemfile**. Gemfile is a file that defines all gems used by the application it is located in **App** directory.

In Gemfile search for rails and change the version number.

after modifying rails version run:
```
bundle install
```
