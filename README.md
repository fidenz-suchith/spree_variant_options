Spree Variant Options spree extension that replaces the radio-button variant selection with groups of option types and values.
In this verson it has modified to dropdowns. So instead of the buttons it'll generate a separate dropdown which contains values for each option type.

current version - spree-2-4-stable

Added Features:
 Dropdowns for each option type.
 Supports multi-currency.


To install Spree Variant Options, just add the following to your Gemfile:

```ruby
gem 'spree_variant_options', :git => 'git://github.com/fidenz-suchith/spree_variant_options.git', :branch => "2-4-stable"
```

Now, bundle up with:

```bash
bundle
```

Next, run the install generator to copy the necessary migration to your project and migrate your database:

```bash
rails g spree_variant_options:install
rake db:migrate
```

------------------------------------------------------------------------------
Configuration Options
------------------------------------------------------------------------------

Spree Variant Options comes with some handy options:

- allow_select_outofstock (default : false)
  When using extension like ([spree_wishlist](https://github.com/spree/spree_wishlist)), you might want to allow your customer to add out of stock product by selecting out of stock variant options :
  ```erb
    <%= form_for Spree::WishedProduct.new, :html => {:"data-form-type" => "variant"} do |f| %>
      <%= f.hidden_field :variant_id, :value => @product.master.id %>
      <button type="submit" class="medium blue awesome">
        <%= t(:add_to_wishlist) %>
      </button>
    <% end %>
  ```
  By setting allow_select_outofstock to true, when a user selects variant options it will automatically update any form's input variant_id with an data-form-type="variant" attribute.

- default_instock (default: false)
  If this is option is set to true, it will automatically preselect in-stock variant options.

- main_option_type_id (default: 1)
  This is the option type id that will be use for showing each variant in the home.
- main_option_type_label (default: 'color')
  This is the option type label that will be use as URL parameter to preselect the option in the product show page.

These configuration options can be set in a config/initializers/spree_variant_options.rb file for example :
```ruby
SpreeVariantOptions::VariantConfig.allow_select_outofstock = true
SpreeVariantOptions::VariantConfig.default_instock = true
```
