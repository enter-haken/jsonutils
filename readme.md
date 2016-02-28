jsonutils
=========

The goal of the `jsonutils` project is to provide console centric json tools

### Functions

#### getExcelSheet

```
usage: getExcelContent [-h] [-f FILENAME] [-s SEPERATOR] [-1] [-t]

get excel sheet content

optional arguments:
  -h, --help            show this help message and exit
  -f FILENAME, --filename FILENAME
                        filename of the excel sheet
  -s SEPERATOR, --seperator SEPERATOR
                        field seperator
  -1, --firstLine       show only first line
  -t, --tail            only content after fist line
```

#### getArray

*getArray* reads json data row per row from stdin. 
If a given field is found in the current row, it is stored in an array.

```
usage: getArray [-h] [-f FIELDNAME] [-s SEPERATOR] [-l LEFTBORDER]
                [-r RIGHTBORDER]

get an arry from a field exists in a list of json documents

optional arguments:
  -h, --help            show this help message and exit
  -f FIELDNAME, --fieldName FIELDNAME
                        field name in json (default: _id)
  -s SEPERATOR, --seperator SEPERATOR
                        specify field seperator (default: , )
  -l LEFTBORDER, --leftBorder LEFTBORDER
                        left border (default: [)
  -r RIGHTBORDER, --rightBorder RIGHTBORDER
                        right border (default: ])
```

For example you have json data like this

```
echo '{ "_id" : 1, text : "Test1" }
{ "_id" : 2, text : "Test2" }
{ "_id" : 3, text : "Test3" }' > testData.json
```

here some sample calls


```
$ cat testData.json | getArray
[1, 2, 3]

$ cat textData.json | getArray - l "(" -r ")"
(1, 2, 3)

$ cat textData.json | getArray - l "(" -r ")" - s "|"
(1|2|3)

cat testData.json | getArray -l "(" -r ")" -s " | " -f text
(Test1 | Test2 | Test3)
```

### Contact

Jan Frederik Hake, <jan_hake@gmx.de>. [@enter_haken](https://twitter.com/enter_haken) on Twitter.
