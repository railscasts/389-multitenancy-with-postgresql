# RailsCasts Episode #389: Multitenancy with PostgreSQL

http://railscasts.com/episodes/389-multitenancy-with-postgresql

Requires Ruby 1.9.2 or higher.


### Commands used in this episode

```
rails db
rails g model tenant subdomain
rake db:migrate
rails c
rails g migration add_sticky_to_topics sticky:boolean
rails g migration add_name_to_tenants name
```

### Commands used in rails console

```ruby
t = Tenant.create! subdomain: "cheese"
c = t.connection
c.execute("create schema tenant1")
c.schema_search_path = "tenant1"
load 'db/schema.rb'
Post.all
Tenant.all
c.execute("drop table tenants")
c.schema_search_path = "tenant1, public"
Tenant.all
Post.all
Tenant.create! subdomain: "chunkybacon"
```

### Commands used in rails dbconsole

```sql
\dt
\dn
create schema foo;
create table foo.items ();
delete from items
delete from foo.items
show search_path;
set search_path to foo, public;
delete from items
drop schema foo cascade
```
