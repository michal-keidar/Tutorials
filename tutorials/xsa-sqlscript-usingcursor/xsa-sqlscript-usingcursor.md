---
title: Using Cursors
description: Leveraging SQLScript in Stored Procedures & User Defined Functions
tags: [  tutorial>intermediate, topic>sql, products>sap-hana, products>sap-hana,-express-edition ]
---
## Prerequisites  
 - **Proficiency:** Intermediate
 - **Tutorials:** [SQL vs Cursors vs Arrays vs Index-based Cell Access](http://go.sap.com/developer/tutorials/xsa-sqlscript-sql-cursor.html)

## Next Steps
 - [Using Arrays](http://go.sap.com/developer/tutorials/xsa-sqlscript-usingarrays.html)

## Details
### You will learn  
This solution leverages a cursor for looping over the rows and calculating the sum and using UNION ALL for building the result set to solve the exercise. It is the slowest running solution out of the three shown possibilities.

### Time to Complete
**15 Min**.

---

1. Use what you have learned and create another procedure called  `calculate_cumulative_sum_of_delivered_products` in the procedures folder. 

	![new procedure](1.png)

2. Be sure to change the namespace from `Undefined` to `dev602.procedures`. Enter the input and output parameters as shown

	![output parameters](2.png) 

3. Enter the following DECLARE statements

	![declare statements](3.png)

4. Enter a FOR loop which will iterate over the input parameter table and perform the calculation and finally update the output table parameter.

	![for loop](4.png)

5. The completed code should look very similar to the following. If you do not wish to type this code, you can reference the solution web page at `http://<hostname>:51013/workshop/admin/ui/exerciseMaster/?workshop=dev602&sub=ex2_20`

	```
	PROCEDURE "dev602.procedures::calculate_cumulative_sum_of_delivered_products" ( 
	```

6. Click “Save”.  

	![save](6.png)

7. Return to the procedure called `get_product_by_filter` and remove the last SELECT statement.

	![remove select](7.png)

8. Insert a call to the procedure called `calculate_cumulative_sum_of_delivered_products` and pass the `aggregated_filtered_items` as the input parameter and set products as the output parameter as shown

	![insert call prcoedure](8.png)

9. Finally, add a SELECT statement at the end to assign the sorted results to the output parameter.

	![select statement](9.png)

10. The completed code should look very similar to this following. If you do not wish to type this code, you can reference the solution web page at `http://<hostname>:51013/workshop/admin/ui/exerciseMaster/?workshop=dev602&sub=ex2_21`

	```
	PROCEDURE "dev602.procedures::get_product_by_filter" (
	```

11. Click "Save".

	![save](11.png)

12. Use what you have learned already and perform a build on your `hdb` module. Then return to the HRTT page and invoke the procedure.

	![HRTT](12.png)

13. make sure to pass the filter string. Note: This procedure call will take a few seconds, just wait for it to return results.

	```
	'CATEGORY = ''Notebooks'' OR CATEGORY = ''PC'''
	```
	
	![filter string](13.png)

14. Eventually, the results will be shown.  

	![results](14.png)

15. You will notice that using cursors takes quite a bit of time. 

	![run time](15.png)
	

## Next Steps
 - [Using Arrays](http://go.sap.com/developer/tutorials/xsa-sqlscript-usingarrays.html)