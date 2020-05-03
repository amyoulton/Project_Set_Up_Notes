# Many to Many Associations

## Creating Users

We will be creating a users model to allow us to add users into our project. An example model:

    users g model user first_name:string last_name:string email:string:index password_digest:string

Remember that models should be singular in name and tables will be pluralized. With this command it will created the model called `user` and it will created a migration for the table `users` with the table data. It should create your migration correctly. Once you confirm that your migration is correct, you need to run:

    rails db:migrate

This had run the migration and has added the table to your database.

## BCrypt Hash

Used to Encrypt a password.
When you hash something, there is no way to reverse it. You can jumble and encrypt it, but there is no way to reverse it and make it readable again.

## Enable Authentication

Uncomment out BCrypt from Development Gems in Gemfile. It already exists in Gemfile as a comment.

    run bundle

In the necessary model (likely user):

    has_secure_password

Since authentication is already built in, adding this method into the model enables authentication.
It adds two attr_accessors :password & :password_confirmation
Adds a prescence validation for password
It will hash passwords automatically and store them in a column called password_digest

This method requires:

- a BCrypt library/gem
- a column in the table called password_digest
