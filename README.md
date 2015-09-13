czMore
======

A JQuery Plugin, that is used to add more fields to a form, it's used when you are adding to a detail on a master file

Quick Start
======
1. Setup HTML Template that you want to be repeated in the details, this template will be cached and removed from you page for when you really need it. as many times as you want to.
	<div id="czContainer">
		<div id="first">
			<div class="recordset">
			<input type="text" name="stock_1_product" id="stock_1_product" />
			</div>
		</div>
	</div>
	
2. Add to the buttom of the page and you are done. 
	<script src="js/jquery.czMore-1.5.3.2.js"></script>
    <script type="text/javascript">
        //One-to-many relationship plugin by Yasir O. Atabani. Copyrights Reserved.
        $("#czContainer").czMore();
    </script>


Notice that the field above has "_1_" in it's name and id, this will be changed to the corrosponding number in the details data set, so if you add 2 there will be two fields "stock_1_product" and "stock_2_product", so you can watch for this as you process the form or do other client-side work