---
title: Creating Scalar User Defined Functions
description: Leveraging SQLScript in Stored Procedures & User Defined Functions
tags: [  tutorial>intermediate, topic>sql, products>sap-hana, products>sap-hana,-express-edition ]
---
## Prerequisites  
 - **Proficiency:** Intermediate
 - **Tutorials:**  [Intermediate Table Variables](http://go.sap.com/developer/tutorials/xsa-sqlscript-table-var.html)

## Next Steps
 - [Creating Table User Defined Functions](http://go.sap.com/developer/tutorials/xsa-sqlscript-table-user.html)

## Details
### You will learn  
In this exercise we are creating a scalar UDF for generating a full name from the last, first and middle name of the employee.

### Time to Complete
**15 Min**.

---

1. Right click on the "procedures" folder and choose "New", then "Function".

	![New Function](1.png)
	
2. Enter the name of the file as `get_full_name` and click "Create".

	![create](2.png)

3. The editor will open with a small code snippet inserted

	![code snippet](3.png)

4. Rename the namespace from `Undefined` to `dev602.procedures`

	![rename](4.png)

5. Enter the code into the editor as shown here.  Please note the default for parameter `im_employeeid` which makes assigning a value to the parameter optional. If you do not wish to type this code, you can reference the solution web page at `http://<hostname>:51013/workshop/admin/ui/exerciseMaster/?workshop=dev602&sub=ex2_13`

	```
	FUNCTION "dev602.procedures::get_full_name" (

6. Click "Save"

	![save](6.png)

7. Return to your procedure called `get_po_header_data` and modify it. Start by renaming the `LOGINNAME` column of the output table to `FULLNAME`. Also change the output length to 256. This is needed to match later on which the anticipated output structure.

	![rename](7.png)

8. Change the last SELECT statement.  Remove the `LOGINNAME` column from the field list and replace it with a call to the scalar function that you created earlier.  Make sure to pass the `NAME.FIRST`, `NAME.MIDDLE` and `NAME.LAST` name columns to the scalar function call.

	![Change select](8.png)

9. The completed code should look very similar to this. If you do not wish to type this code, you can reference the solution web page at `http://<hostname>:51013/workshop/admin/ui/exerciseMaster/?workshop=dev602&sub=ex2_14`

	```
	PROCEDURE "dev602.procedures::get_po_header_data" (
	```

10. Click "Save".

	![Save](10.png)

11. Use what you have learned already and perform a build on your `hdb` module. Then return to the HRTT page and invoke the procedure.

	![Build](11.png)

12. A new SQL tab will be opened, click "Run".

	![Run](12.png)

13. Notice the `FULLNAME` column, it shows the results of the scalar `UDF` logic.

	![Results](13.png)


## Next Steps
 - [Creating Table User Defined Functions](http://go.sap.com/developer/tutorials/xsa-sqlscript-table-user.html)