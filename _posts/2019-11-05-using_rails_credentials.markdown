---
layout: post
title:      "Using Rails Credentials"
date:       2019-11-06 00:48:30 +0000
permalink:  using_rails_credentials
---



A guide on using the Rails built in encrypted credentials storing system, instead of using the dotenv gem and a .env file.

(Needs rails 5.2+)

Uses `config/master.key` and `config/credentials.yml.enc` files which should already be set up with your Rails app.

Your keys will be encrypted and stored in the credentials file. You can use this for API keys, AWS keys, or any values you don’t want to be exposed directly in your code.

The master key is used to encrypt and decrypt these keys, and should already be tagged in your gitignore file, so it will not be made public. When deploying your application to heroku for example, you may then reveal your master key to the heroku server so it is able to decrypt the credentials file.

Make sure `config.require_master_key` in `config/environments/production.rb` is set to `true` for production.

To modify your credentials and add your keys, run the following command in your terminal
```
EDITOR=atom rails credentials:edit
```
This will open a decrypted version of the file using atom. You can also use vim, or any other editor you prefer. When this file is saved, it will update an encrypted version of the credentials file with your master key. If these files don’t exist, Rails will create them for you when running the `rails credentials:edit` command

The structure of the unencrypted file is similar to a normal .yml file. For example:
```
aws:
 access_key_id: 123
 secret_access_key: 345
secret_key_base: 2ffrekjnernremgioodpewkf
```

After setting these credentials, you can access them anywhere in your Rails app with the following syntax.
```
Rails.application.credentials.aws[:access_key_id]     # => "123"
Rails.application.credentials.aws[:secret_access_key] # => "345"
Rails.application.credentials.secret_key_base         # => "2ffr…"
```
This can be used, for example, to access API keys when using Faraday endpoint calls in your Rails controller.

Finally, when deploying to heroku, set a heroku environment variable for your app to reveal your master key to the server. This can be done on heroku’s web dashboard, or through heroku cli as: `heroku config:set RAILS_MASTER_KEY=123456789` (Copy the key from your master.key file) Rails will be able to detect this as the master key to decrypt your credentials for use.

Some helpful blog posts:
[EngineYard](https://www.engineyard.com/blog/rails-encrypted-credentials-on-rails-5.2)
[Medium/cedarcode](https://medium.com/cedarcode/rails-5-2-credentials-9b3324851336)

