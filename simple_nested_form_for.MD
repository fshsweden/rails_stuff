<head>
<link rel="stylesheet" type="text/css" href="github-styles.css">
</head>
<body>

# simple nested form for

# dependencies

## nested_form-0.3.2
*  bundler (>= 0, development)
*  capybara (~> 1.1, development)
*  mocha (>= 0, development)
*  rake (>= 0, development)
*  rspec-rails (~> 2.6, development)

# setup

`Gemfile: gem 'nested-form'`

# complete example


    <%= simple_nested_form_for @zone, html: { class: 'form-horizontal' },

    wrapper: :horizontal_form,
    wrapper_mappings: {
      check_boxes:   :horizontal_radio_and_checkboxes,
      radio_buttons: :horizontal_radio_and_checkboxes,
      file: :horizontal_file_input,
      boolean: :horizontal_boolean
    } do |f| %>

     <%= f.error_notification %>

    <%= f.input :name, :placeholder => 'Name' %>
    <%= f.fields_for :polygons do |builder| %>
      <%= render "polygon_fields", :f => builder %>
      <%= builder.link_to_remove "Remove" %>
    <% end %>
    <%= f.link_to_add "Add a segment", :polygons %>

    <div class="actions">
      <%= f.submit %>
    </div>
    <% end %>


# details

```
class Polygon < ActiveRecord::Base
	belongs_to :zone
end
```
```
class Zone < ActiveRecord::Base
    has_many :polygons
end
```

## sets up a "Remove" link
```
<%= builder.link_to_remove "Remove" %>
```

## sets up a "Add" link
```
<%= f.link_to_add "Add a segment", :polygons %>
```

```
<%= f.input_field :json_points %>
```

# tips and tricks

</body>
