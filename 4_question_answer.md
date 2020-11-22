**About `plural` and `singular`**

Ruby on Rails follow linguistic convention. That means a model represents a single blog, whereas a controller works on all blogs that are in the database table. That is why when generating a controller, rails will automatically create `blogs_controller.rb` file with `BlogsController` class. And when generating a model, rails will automatically generate a model file named `blog.rb`

**About `rake routes`:**

The Rails router recognizes URLs and dispatches them to a controller's action. Rails routes are created based on resources that are available in `routes.rb` file. So, `blog` points to the url of a single blog which redirects to blog show page. `new_blog` points to the new function in blogs controller which redirects to the new blog page. `blogs` points to the index function in blogs controller which redirects to the index page of blogs. And `confirm_blogs` should be `confirm_blog` that calls blog confirmation function.
