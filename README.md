# IDfy---Assignment-Solution
Assignment Readme.


1. The IPAddress assignment from the first coding challenge is commented and explains the logic and flow.

2. The 2nd assignment i.e. Flask_ShoppingCart isn't commented due to time constraints

3. The problem statement and logic behind the implementation are explained below:
	
	- Problem Statement : Build a e-commerce/shopping cart which loads data from a database of products. User should be able to 
				add, said products, to their cart. The program then compares the items in the cart to a database of
				discounts and applies it to the total.
	
	- File to run :
		. app.py
					
	- Implementation Logic:
		. As described, I created a database using sqlite3 which comprised of tables for products, cart, discounts and 
			discount conditions.
		. The program allows user to add products of user specified quantities to the cart.
		. Upon adding items to the cart, the program then calculates the highest possible discount applicable, while 
			avoiding item quantity overflow and redundant discounts, with the constraint of MAX_NO_OF_DISCOUNTS_APPLIED = 3.

	- Ideal Test Case:
		. Add “Product A - Qty = 3”
		. Add “Product B - Qty = 2”
		. Add “Product E - Qty = 2”
		. Check Cart
		. Remove “Product B” and/or “Product E” and view change in discount
	
	- Products table:
	
		|product_id          |product_name|product_price|
		|--------------------|------------|-------------|
		|12120001            |Product A   |199.0        |
		|12120002            |Product B   |399.0        |
		|12120003            |Product C   |449.0        |
		|12120004            |Product D   |499.0        |
		|12120005            |Product E   |249.0        |
		|12120006            |Product F   |249.0   	|
	

	- Discount Conditions tabe:
	
		|condition_id        |condition_verb|itemA_qty |itemA_id  |boolean_condition|itemB_qty |itemB_id  	|
		|--------------------|--------------|----------|----------|-----------------|----------|----------	|
		|1                   |BUYS          |1         |12120001  |AND              |2           12120005  	|
		|2                   |BUYS          |2         |12120001  |AND              |2           12120002  	|
		|3                   |BUYS          |2         |12120002  |AND              |1           12120004  	|
		|4                   |BUYS          |1         |12120003  |AND              |1           12120005	|
	
	
		
	- Discounts table:
	
		|discount_id         |condition_id|discount_price|
		|--------------------|------------|--------------|
		|1                   |1           |199.0         |
		|2                   |2           |249.0         |
		|3                   |3           |149.0         |
		|4                   |4           |99.0        	 |
 
