---
layout: post
title: Submit rails form with a field not in model
---

> This is from [Form field not part of rails db model](https://stackoverflow.com/questions/11060220/form-field-not-part-of-rails-db-model).

You need to pass an attribute in a form, which does not exist in the data base table. This can be done by `Virtual Attributes`.

Let's say you want to deal with an attribute called 'virtual_attribute'. Here is how you would deal with it:

While in your form you would have something like this:

```ruby
<%= f.check_box :virtual_attribute %>
```
In your Model you would have to do this:

```ruby
attr_accessor :virtual_attribute
```

Notice that this is a built-in Ruby method that gives you the setter and the getter for that attribute:

```ruby
#getter
def virtual_attribute
  @virtual_attribute
end

#setter
def virtual_attribute=(value)
  @virtual_attribute = value
end
```

Then you can use the virtual attribute in controller like:

```ruby
params.require(:model_name)[:virtual_attribute]
```
