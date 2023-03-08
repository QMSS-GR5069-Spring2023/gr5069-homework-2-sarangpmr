# homework 5 - create an R package

## Instructions

1. Use data logging NBA player season statistics from the `/data` folder in this repo. Variable descriptions can be found [here](https://www.kaggle.com/drgilermo/nba-players-stats/data).
2. Your final document should be an `.md` file (GitHub-flavored markdown) knitted from an R Markdown file. Create a folder called `/homework` where you will add the `.md` file, and a folder called `/src` where you will  place the `.Rmd` file and any other scripts you used to create the reports.

  In answering each of the questions for the assignment please include
  - the question as a header in your R Markdown report,
  - the raw code that you used to generate any tables, and
  - the top ten rows of the resulting `tibble`. (Do not include more than ten rows for any table in your report).

	Items 1-4 do not require demonstrations in your final report. Your final report demonstrate each function from your library along with its output per item 5 below.

3. when you are done with your final `push` to this repo, submit the link to this repo on Canvas. (Make sure to `commit` your progress throughout the day, and `push` your progress at the end of each day.)


### Assignment items `[100 pts]`

1. `[30 pts]` Create three functions and save them into individual R scripts (.R files).  

	**Function 1:** Your input for this function should be an individual year.  Your output should be a data point of interest in the dataset for some player.

	**Function 2:** Your input for this function should be an individual year.  Your output should be the oldest player in the NBA data for that year (if multiple players have the same age, then decide how to return a single player).

	**Function 3:** Your input for this function should be an individual year.  Your function should limit the data for that year to include numeric continuous variables only (not categorical data).  Your output should be the correlation matrix for all numeric variables in the data for that year.  (Hint: use `cor(data)` to create correlation matrix.  If you feel adventuresome, then you can return a correlogram plot from [here](http://www.sthda.com/english/wiki/visualize-correlation-matrix-using-correlogram) instead).

2. `[20 pts]` Create a package using the `create_package()` function.  Save these .R files into the `/R` folder of your package.  Add roxygen documentation to the top of all .R functions.  Use the `document()` function to auto-create documentation for all functions.  Create a `data/` folder in your package folder to share the NBA data with end users.  (Or use internal data, either way is fine as long as your data is accessible to your package functions.)

	Save the full nba data object to the `data/` folder.  After you save the new data in the data/ folder rerun the `document()` function to document your data.

	Install your package locally.  

3. `[10 pts]` Start a new publicly available repository on your Github account.  `push` your package to your new repository.

4. `[10 pts]`Use the `install_github()` function to install your package in R.  

5. `[30 pts]` Run each of the functions to ensure that they are working correctly in R.
