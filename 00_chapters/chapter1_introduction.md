# Introduction
 
## Background
 
In recent years the number of cars on the road has been on a slow increase, due to more affordable ways of manufacturing them. With the increase of vehicles on the road car-related incidents are on the rise also. 
 
According to a study conducted by the RSA based in Ireland during the period of January - December 2020 there were a total of 137 fatal collisions which resulted in 148 on Irish roads. Which turns out to be a 6% increase of fatalities compared to provisional Garda data collected for the year of 2019 [@RSA_2021].
 
 
 
![Fatalities by year](03_figures/introduction/Road_Deaths.png)
 
You can cite the figure in the text (to match the automatic figure numbering). See Figure \ref{octodog} for a dog version of an octopus!
 
 
(Thanks to Lokikaze for publishing this image on [Deviant Art](http://lokikaze.deviantart.com/art/Octo-Dog-MSPaint-186013612))
 
Here is a bulleted list using minus-signs before each item:
 
- apples
- pears
- bananas
 
Here is a numbered list using `1. ` before each item:
 
1. blue
1. green
1. yellow
1. gold
 
here is some code inline using backticks:. A good loop is `foreach`
 
here are some lines of code using indentation
 
	foreach($cars as $car){
		print $car->getRegistration();
	}
 
To get better syntax highlighing you can triple backtick code blocks and state the language:
 
```php
foreach($cars as $car){
	print $car->getRegistration();
}
```
 
You need to insert empty lines at the end of each section.....  
 
## Other great books
 
There are some great books out here, e.g. see [@hitch_hikers_guide].
 
If you want to learn about Unity game programming try a cookbook [@smith2018].
 
Another sentence typed here.
 
## Example of a Table
 
Below see Table \ref{hugh_et_al}, for a list tech things, and in the Markdown source how to create such a table.
 
<!-- ***************************************************** -->
<!-- ****************** start of table ******************* -->
<!-- ***************************************************** -->
Table: Description of some computing techy things. \label{hugh_et_al}
 
 
Item                 | Description                              | hrs   | rate
---------------------|------------------------------------------|-------|----
Hugo Installation    | Static HTML site generator               | 2     | 180
Database Integration | Testing of data structures               | 2     | 180
SCORM integration    | Connecting to Moodle                     | 6     | 180
Design and CSS       | Design of web page front-end             | 4     | 180
Testing and Tuning   | Ensuring that components are functional  | 3     | 180
                     | Subtotals                                |       |
                     | Discount                                 |       |    
                     | Total (ex. GST)                          |       |
                     | Total (inc. GST)                         |       |
 
<!-- ***************************************************** -->
 
See Figure \ref{md_tables} for how to create tables using MarkDown and a little bit of LaTeX.
 
![MarkDown source code for tables. \label{md_tables}](03_figures/introduction/tables_markdown.png)
 
## Free Online TableConvert.com
 
If you don't want to edit tables manually in MarkDown, a great free online tool that will do this for you is TableConvert. See Figure \ref{table_convert}.
 
- [https://tableconvert.com/?import=example](https://tableconvert.com/?import=example)
 
![Online table Markdown (and LaTeX) creator. \label{table_convert}](03_figures/introduction/table_convert.png){ width=75% }
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzgyMjIxMjIzXX0=
-->