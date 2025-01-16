# list\_files

`list_files() -> [str]`

Returns a list of filenames accessible by the running integration.

```
filenames = list_files() debug(filenames, "available files")
```

Any of the returned filenames can then be used with `open_glyuefile()`&#x20;

```
for name in list_files(): 
    with open_glyuefile(name, "a") as file: 
        file.write("foobar")
```
