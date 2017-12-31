# Update a record from button or link select
source: [ActiveRecord finder method #where not filtering query results](https://stackoverflow.com/questions/47253056/activerecord-finder-method-where-not-filtering-query-results)

In addition to the above post, remember to include a respond_to block in the custom action method for the attribute update

e.g..

```ruby

respond_to do |f|
f.js { redirect_to <..desired_path_goes_here..>
f.html

```

The js gets to respond as the template code includes the ```remote: true``` option
