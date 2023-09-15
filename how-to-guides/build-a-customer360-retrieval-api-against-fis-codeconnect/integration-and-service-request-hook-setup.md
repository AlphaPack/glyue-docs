# Integration and Service Request Hook Setup



**Integration and Service Request Hooks**\
\
From here, there are only a few more things we need to do in order to query the core system for customer information and return it to the source system.\
\
From the previous step, we set the `_path` field mapping row's value to `f"customers/{customerNumber}"` . Essentially, we've established part of the URL path we will be reaching out to in this service request.\
\
The "{customerNumber}" part of that path is a variable we need to set. \
\
Navigate to the Integration Level of the Build page. Open the **Before Hook** of the integration that you've created. Paste the following lines of code into the cell and save your changes:\


```python
customerNumber = "00000000001"
keep(customerNumber = customerNumber)
```

\
The first line sets the customerNumber variable to "00000000001" as an example customer number, but this value can be replaced with a reference to the input payload, such as `input.payload.custNum` as needed.\
\
The second line of code uses the `keep()` function to ensure that this variable is kept in memory and can be used in other parts of the integration, such as the field mapping table where we reference it.\
\
Next, navigate to the service request level of this integration. From here, scroll to the right until you find the column labelled **"After Overall Success Hook"**. Open this column and paste the following line of code into the cell:



```python
output.payload = getCustomer.response.payload
```

\
Essentially, this line of code will take the **response** of the service request to CodeConnect and assign it to the **output** of the Glyue integration. Keep in mind that you will need to replace `getCustomer` with the formula variable you assigned to the service request if you named it differently.
