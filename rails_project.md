### To create a new rails project in entirety:

    rails new <file_name> -d postgresql -T

### If webpacker is not installed:

    rails webpacker:install

### To start the rails server:

    rails s

### To create the database for your rails project (database is named after project):

    rails db:create

### To add other gems into your project for development:

Add them into 'group :development do' method inside of Gemfile within the project,
format them like `gem 'gem-name'`.
Then, once added the required gems, run the following in terminal:

    bundle install

### To create a welcome controller:

    rails generate controller welcome

### To enter the rails repl in terminal:

    rails c

### To generate models:

    rails g model <model-name> <table-field:type> <table-field:type>

Rails will auto generate timestaps.
Running the model will also generate a migration, with the table fields in the migration folder.
The table name will be the plural of the model name you chose.

### To migrate latest/remaining migrations:

    rails db:migrate

This created a schema inside of the db folder.

#### To check the status of migrations:

    rails db:migrate:status

### To reverse the last migration:

    rails db:rollback

### To update fields to existing tables

    rails g migration <name>

#### To add:

    add_column :table_name, :table_field, :data_type

##### Example:

     add_column :questions, :view_count, :integer

#### To remove:

    remove_column :table_name, :table_field, :data_type

##### Example:

    ex. remove_column :questions, :like_count, :integer

### To install faker:

    gem install faker

or add `gem 'faker'` in your gem file, then run `bundle install`

This allows you to create mock seed data for development purposes.

### To run a seed file:

    rails db:seed
