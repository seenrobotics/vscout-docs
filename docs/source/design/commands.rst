Commands and Folder Structure
=============================

Overview
--------

The folder structure of the lib folder and the commands used in vscout are
closely tied to each other, since CLI programs' commands are its actions.

Commands
-----------------

add
```````

type <data type> <data properties>
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
add data type to db

data?  <data type> <data>
'''''''''''''''''''''''''''''''''''''''''''''''''''''''
add data to db with given data type

UX research and existing examples to figure out if data is required in the
command

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

ls
````
type?  <data type>
'''''''''''''''''''''''''''''''''''''
list all members of data type in db

rm
````

type <data type>
'''''''''''''''''''''''''''''''''''''
remove data type from db

show <data type>
```````````````````````````````
graph, or display data type's information
