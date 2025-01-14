# keep

`keep(**kwargs)`&#x20;

Adds all provided arguments to the current integration namespace. Once kept, they can be accessed directly throughout the life of the integration, including in subsequent lifecycle hooks and as values within a field mapping.&#x20;

The keyword given as a variable determines the variable name that's used to access the value subsequently.

```python
a = ["list", "items"]
keep(a=a)

keep(should_create_account = input.payload.create_account)

b, c = [], []
keep(test=b, c=c)

x = {"y": [], "z": []}
keep(**x)
```



Note that mutations to a variable after it is kept are **not** updated within the global namespace. Changes to a variable after it is kept must then be re-kept to persist for later access.

```
# Before hook
keep(foo = 123)
foo += 1

# Finaly hook
debug(foo) # This will print "123"
```
