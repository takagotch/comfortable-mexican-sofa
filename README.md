### comfortable-mexican-sofa
---

https://github.com/comfy/comfortable-mexican-sofa

```
gem 'comfortable_mexican_sofa', '~> 2.0.0'
bundle install
rails g comfy:cms
rake db:migrate

comfy_route :cms_admin, path: "/admin"
comfy_route :cms, path: "/"

rails s

```

```ruby
ComfortableMexicanSofa::AccessControl::AdminAuthntication.username = 'username'
ComfortableMexicanSofa::AccessControl::AdminAuthntication.password = 'password'


```

```
{{ cms:wysiwyg content }}

<html>
  <body>
     <h1>{{ cms:text title }}</h1>
     {{ cms:wysiwyg content }}
  </body>
</html>


{{ cms:textarea content }}
<h1>{{ cms:text header }}</h1>
<div class="row">
  <div class="col-md-6">
    {{ cms:markdown left-column }}
  </div>
  <div class="col-md-6">
    {{ cms:sysiwyg right-column }}
  </div>
</div>

<h1></h1>
<img src="/rails/active_storage/foo/bar">
<div class="row">
  <div class="col-md-6">
    Left Content
  </div>
  <div class="col-md-6">
    Right Content
  </div>
</div>
</div>

<html>
  <body>
    <div class='header'>
      {{ cms:text header }}
    </div>
    <div class='content'>
      {{ cms:markdown content }}
    </div>
    <div class='footer'>
      {{ cms:sinppet footer }}
    </div>
  </body>
</html>

# applicaption.html.haml
!!! html
%html
  %head
    = render 'layout/head'
  %body
    = render 'layout/header'
    .content
      = yeild
    = render 'layout/footer'
    
<h1>{{ cms:text title }}</h1>    
{{ cms:markdown content }}

<div class='left'>{{ cms:markdown left_column }}</div>
<div class='right'>{{ cms:markdown right_column }}</div>

<h1>{{ cms:text title }}</h1>
<div class='left'>{{ cms:markdown left_column }}</div>
<div class='right'>{{ cms:markdown right_column }}</div>

<html>
  <head>
    {{ cms:asset layout_identifier, type: css, as: tag }}
  </head>
  <body>
    {{ cms:asset layout_identifire, type: js, as: tag }}
  </body>
</html>

<html>
  <body>
    {{ cms:markdown content }}
    <div class='footer'>
      {{ cms:snippet copyright }}
    </div>
  </body>
</html>

{{ cms:text example }}
{{ cms:textarea example }}
{{ cms:markdown example }}
{{ cms:number example }}
{{ cms:date example }}
{{ cms:datetime example }}
{{ cms:datetime example, strftime: "at %I:%M%p" }}
{{ cms:checkbox example }}
{{ cms:file example }}
{{ cms:file example, as: image, label: "My Photo", resize: "100x50>", gravity: "center", crop: "100x50+0_0"}}
{{ cms:files example }}
{{ cms:text meta-description, render: false }}

<meta name="description" content="<%= cms_fragment_content("meta-description") %>">






```

```
comfy_csm_render_css GET /cms-css/:site_id/:identifier(/:cache_buster)(.:format)
comfy_csm_render_js GET /cms-js/:site_id/:identifier(/:cache_buster)(.:format)


```










