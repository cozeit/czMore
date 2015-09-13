czMore
======

A JQuery Plugin, that is used to add more fields to a form, it's used when you are adding to a detail on a master file.

This plugin has been used in our internal systems at http://cozeit.com for more than 4 years now, it's very basic, and can be enhanced, but the core functions are very stable and easy to use for us.

Read the wiki for design decisions we have made and why.

Quick Start
======
1. Setup HTML Template that you want to be repeated in the details, this template will be cached and removed from you page for when you really need it. as many times as you want to.

	```html
	<div id="czContainer">
		<div id="first">
			<div class="recordset">
			<input type="text" name="stock_1_product" id="stock_1_product" />
			</div>
		</div>
	</div>
	```
	
2. Add to the buttom of the page and you are done. 

	```javascript
	<script src="js/jquery.czMore-1.5.3.2.js"></script>
	<script type="text/javascript">
		//One-to-many relationship plugin by Yasir O. Atabani. Copyrights Reserved.
		$("#czContainer").czMore();
	</script>
	```


Notice that the field above has "_1_" in it's name and id, this will be changed to the corrosponding number in the details data set, so if you add 2 there will be two fields "stock_1_product" and "stock_2_product", so you can watch for this as you process the form or do other client-side work.

In case you need to know how many fields where added in the client side the plugin drops a field with count of the number that is.

```html
<input id="czContainer_czMore_txtCount" name="czContainer_czMore_txtCount" type="hidden" value="0" size="5" />
```

This field will be named after your container, so that if you use other instances of the plugin in the same page you won't see a problem

Events
======

## onAdd
  This will be excuted when you add new rows or fields
## onLoad
  This will be executed sometime during loading but it's not implemented now
## onDelete
  This will be executed before deleting a row or field
