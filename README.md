czMore
======

A JQuery Plugin, that is used to add more fields to a form, it's used when you are adding to a detail on a master file.

This plugin has been used in our internal systems at [Cozeit, Inc.](http://cozeit.com) for more than 4 years now, it's very basic, and can be enhanced, but the core functions are very stable and easy to use for us.

Read the wiki for design decisions we have made and why.

## Quick Start

1. Setup HTML Template that you want to be repeated in the details, this template will be cached and removed from you page for when you really need it. as many times as you want to.

	```html
	<div id="czContainer">
		<div id="first">
			<div class="recordset">
			<input type="text" name="stock_1_product" id="stock_1_product" />
			</div>
		</div>
	</div>
	<!-- The elements you want repeated must be wrapped in an element with id="recordset" -->
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
<input id="czContainer_czMore_txtCount"
   name="czContainer_czMore_txtCount"
   type="hidden" value="0" size="5" />
```

This field will be named after your container, so that if you use other instances of the plugin in the same page you won't see a problem

## Events

### onAdd
  This will be excuted when you add new rows or fields, this event will pass in the index of the row that is just added
  
```javascript  
$("#czContainer").czMore({
	onAdd: function(index) {
		//Do more events here like triggering select2, autocompelete, and/or any more things,
		//you might want to do after an fresh recordset is attached
	 },
});
```
### onLoad
  This will be executed after loading each element, this event will pass in the index of the row that is just added

```javascript  
$("#czContainer").czMore({
	onLoad: function(index) {
		//Mainly used for then you have a number of record sets that are passed/loaded into html
		//before trigering the czMore plugin, so when looping on the recordsets this evenT
		//will trigger each time it finds an container with id=recordset
	},
});
```
### onDelete
  This will be executed before deleting a row or field, this event will pass in the `data-id` attribute of the row.
  
```javascript  
$("#czContainer").czMore({
	onDelete: function(id) {
		//When a recordset is deleted the data-id attribute is passed to this funciton so you can for 
		//example append it to a list and have it processed by the server after the records are saved
	},
});
```

## Styling
  This plugin sets the default css for the plus and minus buttons you can disable
  the styling like the example below and  then add your own styles using the
`.btnPlus` and `.btnMinus` css classes

```javascript
$('#czContainer').czMore({styleOverride: true})
```

## Max limit
  You can use this option to limit the number of recordsets that can be added
```javascript
$("#czContainer").czMore({
    max: 5
});
```

## Integrating into other libraries
You can integrate with other libraries by running the code after the DOM objects are added
```javascript
$("#czContainer").czMore({
    onAdd: function(index) {
        $("input[id$='_suffix']").select2();
    }
});
```