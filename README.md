![image](./Images/HollywoodSign.png)

# DO be dramatic

**Authors**: Marley Lopez, Andy Shen, John Baumgartner


## Business Problem

Our company wants to create a new movie studio, and is curious what direction to take the debut film. We are charged with exploring the types of movies currently performing well at the box office. We will then translate these findings into actionable insights that the head of our company's new movie studio can use to decide what type of film to make.

## Data Understanding

We analyzed several databases including:
- Box Office Mojo
- IMDB
- Rotten Tomatoes
- TheMovieDB
- The Numbers

These data sets contained information about release dates, domestic gross, worldwide gross, budget, rating, genre, actors, actresses, and directors. We analyzed these datasets to draw several conclusions. 

We found that The Numbers database and Box Office Mojo had similar columns, The Numbers had more entries and more precise data. Similarly, both Rotten Tomatoes and IMDB had genre and rating categories, but IMDB had more entries and more uniform data metrics.

## Data Preparation
First we cleaned The Numbers database so that *release_date* and *movie* were strings, and *production_budget, domestic_gross,* and  *worldwide_gross* became integers.

We created new columns *DG_AI* (domestic gross after inflation) and *PB_AI* (production budget after inflation) to have a more accurate view of movie budget & return within the years.

Next we created a column *season* based off of dates, to be able to view trends based on season.

We also created the feature *ROI* which is *domestic_gross / production_budget.*

Next we joined the IMDB databases we needed, turning *movie_basics* and *movie_ratings* into a dataframe called *joinedIMDB.*

We combined The Numbers database with *joinedIMDB* into our masterdataframe, **movie_df**.

Within this new database, we created binary flags for each of the 19 genres used by IMDB.

Final dataset N = 2203


## Data Analysis

After preparing the data, we used our customized dataset combining The Numbers database, IMDB's "movie_basics", and "movie_ratings" tables, to establish a budget, and analyze which movies have the highest domestic gross and return on investment (ROI) within that budget. We were also interested in what season in a year is most successful for premiers for the given genre.

### Setting the Budget 
![graph1](./Images/WhiskerBudget.png)

We found the 75th percentile of all film budgets within our data set to be $57,120,000. We did this to determine what a new film studio like ours should expect to spend. Using this number, we further filtered our data to exclude films above that budget range. 

### Accentuate the Postive
![graph2](./Images/PosROIbyGenre.png)

The most popular genre to produce with a consistently positive ROI is Drama. 

IMDB defines Drama as: 

    Should contain numerous consecutive scenes of characters portrayed to effect a serious narrative throughout the title, usually involving conflicts and emotions. This can be exaggerated upon to produce melodrama.

### Season Premiere
![graph3](./Images/Season.png)

Summer is the best season to release a Drama. The average ROI for Drama films released in the Summer is near 200%.


### Predicting ROI
![graph4](./Images/LinearRegBudget.png)

We can predict the outcome of a dramatic premier in Summer for a studio working within a budget of $57 million to be a domestic gross of $61 million. 

## Conclusion
![image](./Images/Theater.png)
After conducting data analysis, we recommend our first film be a Drama with a Budget of $57 million, slotted for a summer release date. This has the best probability of commercial success for our business. 


## Further Investigation

- Expand to NLP models and streaming data to study long-term profits of franchises and holiday films.
- Review more recent data to confirm trends.
- Look into international expansion.



## Additional Resources

- <p><a href="https://data.bls.gov/cgi-bin/cpicalc.pl">Government Inflation Calculator</a></p>
- <p><a href="https://help.imdb.com/article/contribution/titles/genres/GZDRMS6R742JRGAG">IMDB Genres</a></p>
- <p><a href="https://americanfilmmarket.com/types-3m-10m-films-break/">Low Budget Hits</a></p>
- <p><a href="https://www.nytimes.com/2023/10/20/business/media/apple-killers-of-the-flower-moon-theaters.html?searchResultPosition=22">Apple's Box Office Strategy</a></p>
- <p><a href="https://independent-magazine.org/2022/10/22/the-demise-of-mid-budget-cinema/">The Demise of Mid-Budget Cinema</a></p>
- <p><a href="https://www.bbc.com/culture/article/20130620-is-china-hollywoods-future">Global Box Office Effect</a></p>
- <p><a href="https://www.nytimes.com/2023/03/13/business/media/a24-oscars-everything-everywhere-the-whale.html">A24 Oscars</a></p>

## For More Information

Please visit our full analysis in our [Jupyter Notebook](./index.ipynb) and  [Slide Presentation](./MoviePresentation.pdf).

For more questions, please feel free to reach us: 

**Marley Lopez | github.com/0le-worm**

**Andy Shen | github.com/ashendy**

**John Baumgartner | github.com/jbaumgit**


## Repository Structure

You are currently in the README.md file. The 'index.ipynb' file contains the jupyter notebook of the explaratory analysis of the given data that provides step-by-step guide to how we came to our conclusion. 'Images' file contains the images used in this file. The images were taken from the internet.

```
├── Data                    <- Data file used in this project
├── Images                  <- Images and Graphs used in this project obtained from external and internal source
├── .gitignore              <- Contains list of files to be ignored from GitHub
├── MoviePresentation.pdf   <- Slide Presentation of the project
├── README.md               <- Contains README file to be reviewed    
└── index.ipynb             <- Jupyter notebook of the project containing codes and analysis
```
