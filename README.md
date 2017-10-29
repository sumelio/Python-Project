# GetCategories


This program has to two objects:
1. Use the GetCategories API from eBay.com to download the entire eBay category tree and store it in a SQLite database. The design of the database schema only has one table.
2. Use a SQLite database to render category trees in HTML. It needs to be valid markup that loads in a browser and  clearly reflects the structure of the tree. I show off some of my mad front-end skills.

The solution is runnable from the command line and operate in two modes corresponding to the tasks above:
1. When given the command-line argument "--rebuild" it uses the GetCategories API to download the category tree and create the SQLite database. 
2. When given the command-line argument "--render <category_id>" it should output a file named <category_id>.html that  contains a simple web page displaying the category tree rooted at the given ID. The tree is rendered from the data in your SQLite database. Do not call the GetCategories API! If the database does not exist or no category with the   given ID could be found the program should exit with an error.
 
 ##        SQLite 

SQLite is a SQL database that lives in a single file. It is a very popular library, and most programming languages contain bindings to it. Part of the challenge is to design a SQL schema to store the category tree. Your schema may contain one or more tables. For each category please store at least the following attributes:

o CategoryID
o CategoryName
o CategoryLevel
o BestOfferEnabled

 
 ##    Sample Session
 

Here is a sample session with the program:

```bash
% ./categories --rebuild
% ./categories --rebuild
% ./categories --render 179281
% ./categories --render 179022
% ls 179281.html
179281.html
% ls 179022.html
179022.html
% ./categories --render 6666666666
No category with ID: 6666666666
```

Example HTML Output:

```bash
/1.html
/39.html
```

 
