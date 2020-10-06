# Heart Disease 
We created two charts in R on the Heart Disease dataset obtained from [here](https://www.kaggle.com/ronitf/heart-disease-uci).
```
library(ggplot2)

# Import the data
heartdata = read.csv("C:\\Users\\Emily Chen\\Documents\\RStudio_Projects\\heart.csv")

# Recoding data
colnames(heartdata) # here we see the first column has a strange name "ï..age" so we rename
names(heartdata)[1] <- "age" # rename the column appropriately
# recode chest pain number with descriptive string - 0: asymptomatic, 1:atypical angina, 2: non-anginal pain, 3:typical angina
heartdata$cp[heartdata$cp == "0"] <- "asymptomatic"
heartdata$cp[heartdata$cp == "1"] <- "atypical angina"
heartdata$cp[heartdata$cp == "2"] <- "non-anginal pain"
heartdata$cp[heartdata$cp == "3"] <- "typical angina"
# make a copy of chest pain type column, and replace each with average blood pressure of the type of chest pain
heartdata2 <- aggregate(trestbps ~ cp, data=heartdata,FUN=mean)
heartdata2

# Column Chart (chest pain type x rest blood pressure)
# layers, aesthetoc, type of graph, coord_cartesian for axis zoom, scale_fill for color palette, labs for labels.
p <- ggplot(data=heartdata2, aes(x=cp, y=trestbps, fill=cp)) + geom_bar(stat="identity", width = 0.6) + coord_cartesian(ylim=c(100,150)) + scale_fill_brewer(palette ="Set2")
p + labs(title="Chest Pain Type and Resting Blood Pressure", subtitle="Average resting blood pressure by each type of chest pain.", x="Chest Pain Type", y="Resting Blood Pressure") + guides(fill=guide_legend(title=NULL))
```



```
# Variable with column chart (age x chest pain type x frequency)
o <- ggplot(data=heartdata, aes(age, fill=cp)) + geom_bar(position=position_dodge()) + scale_x_binned() + scale_fill_brewer(palette ="Set3") 
o + labs(title="Age and Chest Pain Type", subtitle="Frequency of Chest Pain Type within Different Age Groups",x="Age in Years", y="Frequency") + guides(fill=guide_legend(title="Chest Pain Type"))
```



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
