# google python dev BABYNAMES.py problem  
The Social Security administration has this neat data by year of what names are most popular for babies born that year in the USA (see social security baby names).

The files for this exercise are in the "babynames" directory inside google-python-exercises (download the google-python-exercises.zip if you have not already, see Set Up for details). Add your code in babynames.py. The files baby1990.html baby1992.html ... contain raw html, similar to what you get visiting the above social security site. Take a look at the html and think about how you might scrape the data out of it.
For this problem, the source data files are in the babynames/ directory within this repository.

* In the `babynames.py` file, implement the *extract_names(filename)* function which takes the filename of a baby\<year\>.html file and returns the data from the file as a single list -- the year string at the start of the list followed by the name-rank strings in alphabetical order. ['2006', 'Aaliyah 91', 'Aaron 57', 'Abagail 895', ...]. 
* Modify *main()* so it calls your *extract_names()* function and prints what it returns (main already has the code for the command line argument parsing). You will be using regular expressions to parse the html. Note that for parsing webpages in general, regular expressions don't do a good job, but these webpages have a simple and consistent format.

Rather than treat the boy and girl names separately, just lump them all together. In some years, a name appears more than once in the html, but just use one number per name. Optional: make the algorithm smart about this case and choose whichever number is smaller.

Build the program as a series of small milestones, getting each step to run/print something before trying the next step. This is the pattern used by experienced programmers -- build a series of incremental milestones, each with some output to check, rather than building the whole program in one huge step.

Printing the data you have at the end of one milestone helps you think about how to re-structure that data for the next milestone. Python is well suited to this style of incremental development. For example, first get it to the point where it extracts and prints the year and calls `sys.exit(0)`. Here are some suggested milestones:

* Extract all the text from the file and print it
* Find and extract the year and print it
* Extract the names and rank numbers and print them
* Get the names data into a dict and print it
* Build the [year, 'name rank', ... ] list and print it
* Fix `main()` to use the ExtractNames list

Rather than have functions just print to standard out, it is more re-usable to have the function *return* the extracted data, so then the caller has the choice to print it or do something else with it. (You can still print directly from inside your functions for your little experiments during development.)

Have `main()` call `extract_names()` for each command line arg and print a text summary. To make the list into a reasonable looking summary text, here's a clever use of join: `text = '\n'.join(mylist) + '\n'`

The summary text should look like this for each file:

```
2006
Aaliyah 91
Aaron 57
Abagail 895
Abbey 695
Abbie 650
...
```


Add an additional argument in the `extract_names()` function from problem 3 that accepts an S3 file path that, if used with the `summary` argument, will push the summary file to the specified S3 bucket location using an AWS CLI related python library. This is the only non-core Python library you can use.

Save the command that sends the summary file to S3 to a bash script called `babynames.bash`. Use a linux command and the AWS CLI to print the contents of your S3 bucket showing the summary file and save to a file called `results.txt`. Include both files in your Git repo.
$ grep 'Emily ' *.summary





