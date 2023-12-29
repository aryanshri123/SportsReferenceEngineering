# Sports Reference Engineering Internship Prompt Solution
Here is Aryan Shrivastava's solution(s) to Sports Reference's Engineering Internship prompt! In my code I display two separate approaches to obtaining the solution. One that involves the pandas library and another that loads the json into a python dictionary and uses base python from there except for the use of matplotlib to visualize the table. I made sure to add comments to the code for clarity.

## Pandas Approach
To me, this is the recommended approach because of the abstractions that Pandas offers. I first loaded in the contents of a given json into a DataFrame. I reindexed so that I could get the team names on the index (left) as well as the columns and to have them in the same order. At this point, each cell has each pairs win/loss records as a dictionary.\

So, I added the get_wins method to apply to the dataframe. For each cell, it takes the value associated with 'L' and replaces the dictionary with that value. As noted in a comment in the code, we take the 'L' value so that wins are read across rows rather than down columns to stay consistent with the example table's formatting.\

After applying, we are left with the final table as a pandas dataframe. Of course, we can end up saving this table later on when needed.

## Iterative Approach
To me, this is not recommended to the Pandas approach. This is because it introduces time and space complexity that Pandas would otherwise abstract away. However, I wanted to add it as you guys mentinoed that you were interested in seeing us work with data structures, loops, and logic.\

I initially read in the json data into a dictionary (hashmap) called `data`. Our main data structure will be a 2d list (array) where the internal lists will represent the rows. I created a list called `ordering` which contains all the teams in a fixed order. This is important in order to ensure that we get the proper wins/losses in the correct index. Otherwise, it would be difficult to order the final table properly given that python dictionaries are inherently unordered.\

I then start looping through the keys and values in the data dictionary. The first thing that I do is create a new list called `row` where the zeroth index is the team that we are interested in. Having this as the first index allows us to get the matrix like property that we desire.\

Then, I loop through `ordering` within the outer loop. Here, I obtain the wins for a team given the opponent. If I get to a team in `ordering` who does not exist as a key in the `opps` dictionary, then it must be the team we are currently analyzing. That is, we are trying to analyze a team's record vs. itself. In that case, we represent the record with `--`. Otherwise, I simply obtain the wins by accessing that team's wins in the `opps` dictionary. We make sure to manipulate the row list accordingly using `row[i+1]` rather than `row[i]` to account for the fact that we included the team name in the zeroth index.\

At the end, we are left with a 2d array with a team's wins reading across rows.\

Finally, I simply used matplotlib to visualize the table. I know it's a little basic and ugly, but we can always pretty it up once we have the correct underlying structure!

## Thank you
Thank you for the opportunity for me to display my skills. 