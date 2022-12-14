# csharpstring

A general set of classes that provides C# .NET style syntax for python string
manipulations. This project is primarily a learner project, and feedback is welcomed.

## Usage
`from csharpstring import static, instance`

The Static namespace contains static methods from the System.String namespace.
The Instance namespace conatins instance methods from the System.String namespace.
This was done to prevent code from becoming overly complex, and inpreformant as a result.
However this could change in the future, as I'm not a fan of its implementation.

## Static Methods
### Join( joinChar, string1, string2 )
Joins string1 and string2 with joinChar

`print(static.join("-","Hyper","Inflation"))`

Produces `Hyper-Inflation`

### Format(stringFormat, *args)
Creates formated text in a way similar to System.String.Format()
```
date = 12/12/2022
time = 1:40PM
print(static.Format("It is $0 on $1.", time, date))
```
Produces: `It is 1:40PM on 12/12/2022`

## Instance Methods
Care is taken so that the objects created by this class still act like 
normal python strings insofar as len(), and str() still work on them, further
compatility is planned.

### Substr(offset, end=None)
The substring method takes a manditory argument of the start position, and an optional
position of the end position. If a second argument is not supplied, the end of the string
is used.
```
strMyString = instance("The quick brown fox jumped over the lazy dog.")
strDog = strMyString.Substr(17,19)
print (strDog)
```
Produces: `fox`

### IndexOf(string)
Searches the string for the fist instance of `string` and returns an integer position
of that string at its start point (when string contains multiple letters).
```
index = strMyString.IndexOf("fox")
print(index)
```
Produces: `17`

### Split(delimiter)
Splits a stting into a list delimited by a supplied character.
```
data = []
count = 0;
f = open('/opt/appdir/config')
lines = f.readlines()
for line in lines:
    entry = instance(line)
    data[count] tuple(entry.Split(":"))
    count += 1;
```

Produces a list of tuples created by reading a colon-seperated file. Each tuple 
containing a single line of the file spliting that line at a single colon. Great for 
reading simple configuration files and the like.

### Append(string)
Appends `string` to the current string, seperated by a space.

### Prepend(string)
Prepends `string` to the current string seperated by a space.

```
half1 = instance("The quick brown fox")
half2 = instance("jumped over the lazy dog")
print(half1.Append(half2));
print(half2.Prepend(half1));
```
Produces `The quick brown fox jumped over the lazy dog` in both cases.

### Replace(substr, replacement)
Searches the string instance for `substr` and replaces it with `replacement`

```
sentance = half1.Append(half2);
print(sentance.Replace("quick", "speedy"))
```
Produces: `The speedy brown fox jumped over the lazy dog`

### ToString()
The `ToString()` method is more for C# compliance.
```
print(half1.ToString())
print(str(half1))
```
Produces the same output.

### SetText(string)
Sets the internal text value of the object to `string`. You will likely never need this
as this value is set in the constructor.

### _Update()
used internally to update the length property and any other state specific data.

### Length
Holds the length of the string. Treat as readonly.

### data
Holds the actual string being manipulated, you should not change this value directly,
as it will cause Length and len(object) to return incorrect values. use `SetText(string)`
instead.








