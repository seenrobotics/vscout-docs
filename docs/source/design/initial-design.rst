Initial Design
===================

1 Background
------------------

Introduction
`````````````````````
vscout is an open source software suite attempting to simplify and enhance
scouting for all robotics teams. This can help teams pick alliance partners,
generate strategies against opponents, and know this information in real time.
It also is designed to be easy to use and significantly more time efficient for
the scout's organization compared to traditional methods. Customizability is a
key factor influencing the design of this software suite, allowing the end user
to collect any data they would like.

Features of Final Solution
````````````````````````````````````
- Cross-Platform

From a Windows, Linux, MacOS, Android, Oak OS, Fuschia OS or iOS device,
one should be able to easily input data through their respective GUIs (web
and mobile) or CLIs (desktop only).

- Data Administration

The data will be available to those specified by administrators of that
particular instance of the data set. This allows some users to only read
data, some users to have full access, and some users to have no access.

- Data Analysis

Through machine learning and/or data analysis, a user can choose to let
their device compute expected statistics like expected autonomous paths.

- Flexible

There is no limit or minimum requirement to the number of devices used
to collect and store data. The software can store any type of quantitative
data, and be able to display statistics in the user's desired way.

- Easy to Use

vscout focuses heavily on UX Design, so if there are any UX issues, it will
be a top priority to fix. It uses Material Design by Google, which is an
established and researched set of design practices to have natural, easy
to use UIs.

- Real Time

Data is available in real-time and can be visually shown in the form of
a graph or any type of visual representation appropriate for that type of
data.

Problem
``````````````

With regular scouting, there is no established good practices or methods to
scout. Oftentimes, beginners are left to scout, since they cannot contribute
to the robot or talk about the robot in great depth. More often than not, these
beginner scouts will not be able to do a proper job without some training. With
vscout, the job of scouting should be effortless, efficient, and data-driven.
Extra scouts can gather the same information about the same match, and
reduce bias efficiently. For experienced scouts, the ability to gather, and
analyze data efficiently is what differentiates vscout from regular scouting.

Non-Goals
```````````

vscout is not a replacement for scouts, and is a tool for them to use to make
their job more efficient. vscout does allow the option for text input for some
qualitative data, but its use case benefits much more from quantitative data.

2 Milestones
-------------------

V1
`````

Our MVP is a CLI and mobile app that can store and perform basic analysis
on many forms of data by itself on one device. There should be the option
to have multiple data sets.

V2
`````

Version 2 should allow multiple instances of local databases (different
devices) to be synced and allow for data administration.

V3
`````

This version should help predict various statistics and include more
rigorous data analysis. There will also be integration with VEX DB if
connected to the Internet to get match statistics automatically.

3 CLI Language
-----------------------

Python
````````````
- Click Library
- Developers already familiar
- Very easy to develop in
- Scripting language
- Consistent SQL database if using SQLite

Dart
`````````

- Flutter cross-platform UI toolkit
- Args and cli_util libraries
- Will get developers familiar with Dart for Flutter app
- Consistent SQL or NoSQL database if using both SQLite or sembast
- Hot reload
- Smooth and fast
- Easy to learn

Decision
```````````````

Dart
'''''''''

Although the click library for Python is amazing for making CLI programs,
and Python networking libraries are top notch, the Flutter framework for
mobile is amazing. It supports all top mobile platforms including the
myserious, upcoming Fuschia OS. With one code base, development time
is saved, and with easily customizable Material Design, the UI will be easy
to customize. Dart itself is not a bad language and is heavily web-oriented.
Its async library is top notch and it has support for a NoSQL and SQL
database through these libraries: Sembast, and SQLite. It is possible to write
CLI programs in Dart, so the logic from the CLI programs can be transferred
directly to the Flutter-based mobile app. If we implement an MVC design
pattern, this might aid the transfer of logic.

4 SQL vs NoSQL
-----------------------

Sembast and vs SQLite

SQL
``````
- Uses SQL
- Very powerful
- Very versatile
- Widely used
- Pre-defined schemas
- All data must follow same structure
- Up front preparation
- Change in structure is disruptive and difficult
- Vertically scalable
- Table-based
- Powerful Queries
- SportsDB super complex structure


NoSQL
````````````
- Dynamic schema for unstructured data
- Can create documents without having to first define structure
- Each document can have unique structure
- Syntax can vary between databases
- Add fields as you go
- Horizontally scalable
- Data stored in many ways: column, document, graph or KV
- No standard interface to perform complex queries
- Queries themselves are not as powerful

Decision
`````````````````

NoSQL
'''''''''''''''

SportsDB is very, very, very complicated, and very hard to properly
grasp. Implementing it is not too hard since they provide the source
on their website. Working with the data from SportsDB would be a
huge challenge. The reason it is so complicated is due to the fact
that it can be flexible. NoSQL is flexible but less complicated, so it
is much better for this use case. Although NoSQL's queries are not
as powerful, this should not pose a problem with proper data
structures. With NoSQL databases, the user will have no issue during
a new season, since the database will not need updating every season.
It also will help when the user customizes what data they want to collect.

5 Distributed vs Centralized
----------------------------------------

Distributed
```````````````````
- Master copy on client
- Harder to understand
- Harder to abstract
- Less likely to have permanent loss of data from one failure
- Always be able to show data from own device
- Can be disconnected
- Local actions are fast since it’s local over requesting server
- Changes can be sent whenever

Centralized
`````````````````````

- Easier to make
- Single master copy on one device (server)
- Access control easier
- Must request centralized server for current dataset

Decision
```````````````

Distributed
''''''''''''''''''''''''

A centralized system makes the user experience much worse, so
the end user may find vscout too complicated, and revert back to
regular scouting without the app. Although a distributed system is
more complicated to build, it is the far superior solution. One thing
to consider is having a distributed system but have one machine have
the master copy of the information, so mimicking a centralized system.
This can be explored later during the development of V2.

6 Method of Making Changes to Database
--------------------------------------------------------------

Local and Sync
`````````````````````````

- No dependency on connection to remote server
- Individuality
- Helps development cycle
- Faster transactions
- Less data loss

Queuing changes to Remote
````````````````````````````````````````````````

- Based on a client server model that users may not understand
- Simple

Decision
```````````````

Local and Sync
'''''''''''''''''''''''''''''''

Although having local databases in each device and syncing each
one is a complex task, it guarantees fast transactions with the
database, and minimizes data loss. This added complexity is
what differentiates a moderate product from a great one.
