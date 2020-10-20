## Kickstarter Projects Dataset
Created a visualization on Kickstarter projects using ggplot2 in R. Dataset obtained from [here](https://www.kaggle.com/kemical/kickstarter-projects).

    library(ggplot2)
    library(RColorBrewer)
    
    # Load data
    kickstarterdata = read.csv("C:\\Users\\Emily Chen\\Documents\\RStudio_Projects\\kickstarter-projects-2018.csv")
    # Data exploration
    summary(kickstarterdata)
    head(kickstarterdata)
    min(kickstarterdata$launched) # todo: remove 1970 "null" values
    # Remove undefined/impossible values
    # Remove 1970 attributes, as well as those with undefined state.
    kickstarterdata2<-kickstarterdata[!(kickstarterdata$launched == "1970-01-01 01:00:00" | kickstarterdata$state == "undefined"),]
    min(kickstarterdata2$launched)

    brewer.pal(12, "Set2")
    display.brewer.pal(12, "Set2")
    colors <- c("canceled" = "#E78AC3", "failed" = "#FC8D62", "live" = "#8DA0CB", "successful" = "#66C2A5", "suspended" = "#B3B3B3")


    d <- ggplot(data = kickstarterdata2, 
                mapping = aes(main_category))
    d + geom_bar(aes(fill = state), colour = "black") + theme_bw() + 
      scale_fill_manual(values = colors) + 
      labs(title = "Kickstarter Projects Results by Category",
           subtitle = "(2009-2018)", 
           x = "Category",
           y = "Number of Projects") + guides(fill=guide_legend(title="Status"))
          
![Kickstarter Projects Figure](https://emilc-jpg.github.io/datavisualization/files/kickstarterdata1.png)  





## US Trending Videos Dataset
Created two charts, this time in Python on the US Trending Videos dataset obtained from [here](https://www.kaggle.com/datasnaek/youtube-new?select=USvideos.csv)

    import pandas as pd
    import numpy as np
    from matplotlib import pyplot as plt
    import seaborn as sns
    from seaborn import lineplot
    
    # Import dataset
    df = pd.read_csv('USvideos.csv', index_col=0)
    df.head()

    sns.set(style="dark")
    # Line Chart (views over time)
    f = lineplot(x='trending_date', y='views', data=df)
    plt.title('Number of views over time in US trending videos')
    plt.show()

![US Trending Videos Chart 1](https://emilc-jpg.github.io/datavisualization/files/USvideos1.png)

    # Line histogram (likes versus dislikes)
    grid = sns.lmplot('likes','dislikes', df, size=7, truncate=True)
    plt.title('Relationship between likes and dislikes in US trending videos')
    plt.show()
![US Trending Videos Chart 2](https://emilc-jpg.github.io/datavisualization/files/USvideos2.png)

## Health Disease Dataset
I created two charts in R on the Heart Disease dataset obtained from [here](https://www.kaggle.com/ronitf/heart-disease-uci).

First, we start with importing the data and recoding some of the values into more descriptive categories.

    library(ggplot2)

    heartdata = read.csv("C:\\Users\\Emily Chen\\Documents\\RStudio_Projects\\heart.csv")

    colnames(heartdata) # here we see the first column has a strange name "ï..age" so we rename
    names(heartdata)[1] <- "age" # rename the column appropriately
    heartdata$cp[heartdata$cp == "0"] <- "asymptomatic"
    heartdata$cp[heartdata$cp == "1"] <- "atypical angina
    heartdata$cp[heartdata$cp == "2"] <- "non-anginal pain"
    heartdata$cp[heartdata$cp == "3"] <- "typical angina"
    heartdata2 <- aggregate(trestbps ~ cp, data=heartdata,FUN=mean)
    heartdata2

Now we are ready to make our charts!


    # Column Chart (chest pain type x rest blood pressure)
    # layers, aesthetoc, type of graph, coord_cartesian for axis zoom, scale_fill for color palette, labs for 
    labels.
    p <- ggplot(data=heartdata2, aes(x=cp, y=trestbps, fill=cp)) + geom_bar(stat="identity", width = 0.6) + 
    coord_cartesian(ylim=c(100,150)) + scale_fill_brewer(palette ="Set2")
    p + labs(title="Chest Pain Type and Resting Blood Pressure", subtitle="Average resting blood pressure by 
    each type of chest pain.", x="Chest Pain Type", y="Resting Blood Pressure") + 
    guides(fill=guide_legend(title=NULL))


![Heart Disease Chart 1](https://emilc-jpg.github.io/datavisualization/files/heartdatachart1.png)
 

    # Variable with column chart (age x chest pain type x frequency)
    o <- ggplot(data=heartdata, aes(age, fill=cp)) + geom_bar(position=position_dodge()) + scale_x_binned() + 
    scale_fill_brewer(palette ="Set3") 
    o + labs(title="Age and Chest Pain Type", subtitle="Frequency of Chest Pain Type within Different Age 
    Groups", x="Age in Years", y="Frequency") + guides(fill=guide_legend(title="Chest Pain Type"))

![Heart Disease Chart 2](https://emilc-jpg.github.io/datavisualization/files/heartdatachart2.png)





## Stephen Malinowski’s Bach, Fugue in A minor, BWV 904 Visualization Review

[Review](https://emilc-jpg.github.io/datavisualization/files/stephenmalinowski-review.pdf)


## COVID-19 Symptoms and Similarities Project Proposal
[Project Proposal](https://docs.google.com/presentation/d/1YSx9sqOEBDdrs0fYi7pW-t5AgNWZdpamZwOohceYotI/edit?usp=sharing)



## Teaching to See
- Difference between geometric accuracy and optical accuracy
- Usage of negative space for balance and harmony
- Importance of common structure and evenness throughout piece
- Sufficiently distinct objects to ensure readability 
- Proper optical spacing between objects with usage of rhythm and color
- Using color intelligently: balance of hue, saturation to convey different messages
- Different types of info can live together without harming each other
- Objective to capture attention of someone walking by
- Should entice to look at more detailed information
- For data visualization, sparking knowledge and curiousity for audience 

[Full Review](https://emilc-jpg.github.io/datavisualization/files/teachingtosee-review.pdf)



## Journalism in the Age of Data

[Review](https://emilc-jpg.github.io/datavisualization/files/ageofdata-review.pdf)













## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/emilc-jpg/datavisualization/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/emilc-jpg/datavisualization/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
