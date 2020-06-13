# Module 4, Lesson 4: Burrow Wheeler transform

https://academic.oup.com/bioinformatics/article/24/6/791/193908

```python
function BWT (string s):
    create a table, rows are all possible rotations of s
    sort rows alphabetically
    return (last column of the table)
```

```python
function inverseBWT (string s):
    create empty table
    repeat length(s) times
        # first insert creates first column
        insert s as a column of table before first column of the table
        sort rows of the table alphabetically
    return (row that ends with the 'EOF' character)
```
