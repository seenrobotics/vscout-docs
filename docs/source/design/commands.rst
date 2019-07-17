Commands and Folder Structure
=============================

Overview
--------

The folder structure of the lib folder and the commands used in vscout are
closely tied to each other, since CLI programs' commands are its actions.

Vocabulary
-----------------

Attribute
``````````````````
An attribute is a classification for data. This is very similar, but different
to data types. Attributes use data types to store data, but have their own
names. For example: the attribute **Shooting Position** will use the data
type **Point**. **Point** is a custom data type that will be made specifically
for vscout, but if need be, primitive data types can also be used. For example:
the attribute **Team** will use the type **String**.

Data type
`````````````````
Funnily enough, a data type according to Wikipedia is an attribute
of data which tells the compiler or interpreter how the programmer
intends to use the data. Some examples of primitive data types in Dart
are: int, double, and bool. Composite data types will make up most of
our custom data types like: Point [int, int], Temporal Point [int, int, int],
or maybe even Temporal Point List [[int, int, int]]

Commands
-----------------

add
```````

attribute <attribute> <data-type>
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
add attribute to db

data <json-text>
'''''''''''''''''''''''''''''''''''''''''''''''''''''''
add data in the json format to db


file <jsonfile>
'''''''''''''''''''''''''''''''''''''''''''''''''''''''
add json file's contents to db

config <configuration option>
````````````````````````````````````````````````````
configure given configuration option

*Adjustable defaults:*
    - Path to db
    - Graph options

find
````````
figure out queries later

init <project-name>
``````````````````````````````````
initialize db

rm
````

attribute <attribute>
'''''''''''''''''''''''''''''''''''''
remove attribute from db

show
```````````
figure this out after find

update
```````````````
figure this out after find
