# Working With Files

## Opening & Closing Files
The following code is probably pretty self-explanatory:
using the `read()` function you get a file object
(actually `TextIOWrapper`) and can then read the file's content
- we will get more into that later.

Also, make sure to close the file after it is no longer needed.

```python
# "r" opens the file in read-only mode
f = open("file.txt", "r")
content = f.read()
print(content)
f.close()
```

```
This is the file's content.
```

As you can see, opening and closing files is quite simple and using the
`with` context manager makes it even easier as it automatically
closes the file at the end of it:

```python
with open("file.txt", "r") as f:
    content = f.read()
    print(content)
    print(f"The file is {'closed' if f.closed else 'open'}")

# outside the context manager
print(f"The file is {'closed' if f.closed else 'open'}")
```

```
This is the file's content.
The file is open
The file is closed
```

## Reading Files

All of the following methods **change the SPI**, the stream position indicator, so the 'current position of the cursor within the file'.

If you read parts of the file, the SPI moves. If you then use another read method, it will start where the old one left off.

### Get the current SPI position
```python
f.tell()
```

### Set the SPI position
```python
f.seek(idx)
```
idx=0 sets the SPI to the beginning of the file

### Read whole file as string
```python
f.read() -> str
```

### Read one line (till next linebreak)
```python
{f.readline() -> str
```

### Read whole file as list of lines
```python
f.readlines() -> []
```
Useful to iterate over a file's lines: `for line in f.readlines(): # ...`

Example:
```python
with open("multiline_file.txt") as f:
    print(f.read())
    f.seek(0)  # reset stream position
    print("----------")

    print(f.readline(), end="")
    print(f.readline(), end="")
    f.seek(0)  # reset stream position
    print("----------")

    print(f.readlines())
```

```
This is a text file.
It contains multiple lines,
as you can see.
----------
This is a text file.
It contains multiple lines,
----------
['This is a text file.\n', 'It contains multiple lines,\n', 'as you can see.']
```

`end=""` parameter of the `print()` function
removes the `\n` that would usually be printed at the end of the line. 
As the read line already contains a line break, I didn't print the extra one from the
`print()` function.
