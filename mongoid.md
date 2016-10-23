### When i try to connect my rails app to mongo lab, i get a trouble.
In config/mongoid.yml
```yaml
  development:
  sessions:
    default:
      username: <user>
      password: <pass>
      database: <data>
      hosts:
        - ds023xxx.mlab.com
      port: 23xxx
```
and i can't access to my database
```shell
  oped::Errors::ConnectionFailure: Could not connect to a primary node for replica set 
  #<Moped::Cluster:30329540 @seeds=[<Moped::Node resolved_address="104.197.61.113:27017">]>
```
Fixed
```yaml
  development:
  sessions:
    default:
      username: <user>
      password: <pass>
      database: <data>
      hosts:
        - ds023xxx.mlab.com:23xxx
```
it worked

so stupid

####Ruby on rails with mongoid
`
  Cannot load `Rails.application.database_configuration`: Could not load database configuration. No such file - ["config/database.yml"]
`
In `config/application.rb` remove `require 'rails/all'`, replace it

  to (in Rails 3.x):
  
  ```ruby
    require "action_controller/railtie"
    require "action_mailer/railtie"
    require "active_resource/railtie"
    require "rails/test_unit/railtie"
    # require "sprockets/railtie" # Uncomment this line for Rails 3.1+
  ```
  
  or (in Rails 4.x):
  
  ```ruby
    # Pick the frameworks you want:
    # require "active_record/railtie"
    require "action_controller/railtie"
    require "action_mailer/railtie"
    require "sprockets/railtie"
    require "rails/test_unit/railtie"
  ```
