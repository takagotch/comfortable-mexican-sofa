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

comfy_route :cms, path: "/:locale/"

# application_controller.rb
before_action :set_locale
def set_locale
  if params[:locale].present?
    I18n.locale = params[:locale]
  else
    I18n.locale = I18n.default_locale
  end
end

config.revisions_limit = 25

class YourCustomModel < ActiveRecord::Base
  cms_is_categorized
end


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

{{ cms:text title }}
{{ cms:text description }}
{{ cms:text open_graph_description, namespace: OG }}
{{ cms:text open_graph_title, namespace: OG }}

{{ cms:sinppet identifier }}

{{ cms:helper some_helper, param_a, key: param_b }}
{{ cms:partial "path/to/partial", local_var: "value" }}

<%= render partial "path/to/partial", locals: {"local_var" => "value"} %>

{{ cms:file_link file_id }}
{{ cms:file graphic, render: false }}
{{ cms:files attachments, render: false }}

{{ cms:page_file_link graphic }}
{{ cms:page_file_link attachments, filename: "cat.jpg" }}

{{cms:asset layout_identifier, type: css, as: tag}}

- Comfy::Cms::Snippet.for_category('carousel').each do |slide|
  .slide= slide.content
  
- @cms_site.snippets.for_category('carousel')

= render "comfy/admin/cms/categories/index", type: "YourCustomModel"
= render 'comfy/admin/cms/categories/form', form: form


```

```
comfy_csm_render_css GET /cms-css/:site_id/:identifier(/:cache_buster)(.:format)
comfy_csm_render_js GET /cms-js/:site_id/:identifier(/:cache_buster)(.:format)

your_locale:
  comfy:
    cms:
      content:
        tag:
          foo: Localized Foo
        namespace:
          bar: Localized Bar
          

```










