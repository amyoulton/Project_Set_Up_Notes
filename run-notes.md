# Terminal Commands for Rails:

# To create a new rails project in entirety:

rails new <file_name> -d postgresql -T

# If webpacker is not installed:

rails webpacker:install

# To start the rails server:

rails s

# To create the database for your rails project (database is named after project):

rails create:db

# To add other gems into your project for development

# Add them into 'group :development do' method inside of Gemfile within the project

# format them like gem 'gem-name'

# Then, once added the required gems, run the following in terminal:

bundle install

# To create a welcome controller:

rails generate controller welcome

# To enter the rails repl in terminal:

rails c
