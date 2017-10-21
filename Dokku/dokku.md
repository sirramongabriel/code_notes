#####RUN A COMMAND IN AN APP ENVIRONMENT
``` ruby
dokku run <app_name> <command>
```
- example: <i>```dokku run sample_app rake db:drop```</i>

#####ENTER RUNNING DOKKU CONTAINER
``` ruby
dokku enter <app_name> [options]= --container-id <pid>  
```

- example: <i>```dokku enter sample_app --container-id 0cc9f9e30240```</i>

or 

``` ruby
dokku enter <app_name> <container_type>
```

   - example: <i>```dokku enter sample_app web```</i>

   
##### Run sidekiq as a separate worker process

``` ruby
dokku ps:scale <app_name> worker=1
```

##### Redis server CannotConnectError

Run redis in the background

``` ruby
redis-server &
```
