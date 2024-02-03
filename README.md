To update the product form to support dynamic checkout buttons
 

 

From your Shopify admin, go to Online Store > Themes.
Find the theme you want to edit, and then click Actions > Edit code.
In the Sections directory, open one of the following files:

Click product-template.liquid to update the product page template. In some themes, the product template has a different filename. In some cases, the product form is included in a file in the Snippets directory, and has a name like product-form.liquid.
Click featured-product.liquid to update the home page featured product section.

Find the product form by searching for <form action="/cart/add". Take note of any attributes that the form has, such as a class or an id. You can include these attributes in the updated product form that you will create in the next step. If you don't include the attributes, then the styling or behavior of the form might be affected.
Delete the entire opening <form> tag, and replace it with the following Liquid:

{% form 'product', product %}
 

To include the attributes from the old form, add them to your updated form by using the following syntax:

{% form 'product', product, id: "oldID", class: "old-class" %}
 

To learn more about modifying form attributes, see the Liquid reference for form tags.

Find the closing </form> tag by searching for </form>.
Replace the closing </form> tag with the following Liquid:

{% endform %}
 

Find the Add to cart button by searching for an input or a button tag that has the attribute type="submit".
On a new line below the Add to cart button, add the following Liquid:

{{ form | payment_button }}
 

Click Save.

Your modified product form should look something like this example code:

{% form 'product', product %}
  ...
  <button type="submit">Add to cart</button>
  {{ form | payment_button }}
  ...
{% endform %}
