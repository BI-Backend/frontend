Introduction
============
This document details the various components of the system and the descriptions of each

Components
==========
Projects
--------
A project is a grouping of **data sources** and **endpoints** that would generally relate to a single dashboard. Each
project has its own permissions and authentication.

Data Sources
------------
A data source belongs to a **project.**  A data source defines a connection to an external provider of data such as a
database, external API, file on disk.etc.  Data sources should be expandable to connect to all manner of different
sources and each type of data source can have its own set of parameters/configuration options.  All data sources should
have the same external interface - initially this would be a set of values for variables exposed by the data source and
will return a value (probably a list/dict/single value or possibly iterators for large amounts of data).

Endpoint
--------
An endpoint serves as the interface between a HTTP request and a **data source.**  In its simplest form, a data source
would simply define a mapping between request parameters and the variables exposed by the data source.  A more advanced
form could define custom python code for manipulating data of one or more **data sources** into a single output. Data
sources would be exposed to the python code through a function that can be called by the user.  All custom python code
will be executed in a sandbox provided by Docker.