### comfortable-mexican-sofa
---

https://github.com/comfy/comfortable-mexican-sofa

```
gem "", ""
bundle install
rails g comfy:cms
rake db:migrate

comfy_route :cms_admin, path: "/admin"
comfy_route :cms, path: "/"



```

```ruby

```

```
<html>
  <body>
     <h1>{{ cms:text title }}</h1>
     {{ cms:wysiwyg content }}
  </body>
</html>

```


