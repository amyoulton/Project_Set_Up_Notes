# BCrypt Hash

Used to Encrypt a password.
When you has something, there is no way to reverse it. You can jumble and encrypt it, but there is no way to reverse it and make it readable again.

# Enable Authentication

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
