---
title: "GitHub-RMarkdown Tutorial"
author: "Gotanda Lab"
date: "2023-04-10"
output: 
  html_document: 
    keep_md: yes
---

# GitHub and RMarkDown Tutorial

Welcome! This will be a bumpy ride but we'll get through it together.

## First things first

Here's what I'd like to cover in this tutorial:

1.  Why use GitHub
2.  Why use RMD
3.  Installing Git
4.  Connecting RStudio to GitHub
5.  Cloning a repository
6.  Your first RMD script
7.  Formatting in RMD
8.  Coding in RMD
9.  Creating a new repository
10. Resources

**Let's get to it!**

------------------------------------------------------------------------

## 1. Why use GitHub?

GitHub is a great tool for keeping track of edits, collaborating on projects and (so) much more.\
It keeps your files on GitHub as well as your computer, and therefore your files are always backed up.\
It also makes your work more accessible to others, as your repositories can be made public and available to other researchers, reviewers, collaborators, etc\

The workflow when working is simple:\
$Pull -> Work -> Pull -> Commit -> Push$

I'll explain the terminology in a bit, but a **"Pull"** pulls what is in the repository (in case there were changes made) into your local folder.\
A **"Commit"** saves your work in the local folder.\
A **"Push"** sends your new work to the GitHub repository.

![](./Figures/Terminology.png)

## 2. Why use RMD?

RMarkdown is fantastic for showing your R scripts to someone. It makes your work repeatable, simple to see, and reduces the chance that your script encounters problems such as different R versions, packages and the many other headaches you get when trying to show scripts.\
In simple terms, it makes sharing R scripts easier.\
That being said, you can do much more than write scripts in RMD. **This tutorial was made in RMD!**\
It runs off the same language Obsidian does, and therefore the same language for formatting. Don't worry, I'll have a refresher when we're dealing with RMD.

------------------------------------------------------------------------

## 3. Installing Git

You don't have to do this right now. I will make this tutorial available for you. **However**, doing this together is better than doing it alone.

**This is considered the worst part of using GitHub. I'll keep this as painless as possible**

### 3.1 Make a GitHub Account

Go to GitHub and make an account (<https://github.com>)

> Remember, your username will be public!

As students, we have access to GitHub Pro, which includes goodies like free private repositories, more storage and advanced tools.

If that interests you, click [here](https://education.github.com/discount_requests/application) once you've made an account.

### 3.2 Actually installing Git

**MAKE SURE YOU ARE USING THE CURRENT VERSION OF R**\
This might come as a surprise, but there's yet another version of R. Try and keep up to date, since many packages require the more recent versions.\
If you are not sure, run the following commands in R:


```r
R.version.string
```

```
## [1] "R version 4.2.3 (2023-03-15 ucrt)"
```

> You should be running version 4.2.3.\

Your next step will be to install Git.

**If you are using Windows** [Install "Git for Windows"](https://gitforwindows.org)

Git prefers to be installed in "Program Files", so unless you have good reason for it, don't change the default folder it wants to make.

**If you are using macOS** Press "F4" or click on the rocket ship in your Launchpad. Type "Terminal" then enter.

Run the following commands:


```r
git --version
git config
```

Click on "Install" and you should be done.

### 3.3 Some finishing up

First, open up the shell. To do this open "Git Bash" (windows) or the terminal (mac).

Let's set our names to match those on GitHub. Run these following commands:


```r
git config --global user.name '[Your name]'
git config --global user.email '[the GitHub email]'
git config --global --list
```

**You MUST use the same email as your GitHub account**

This will help you track who made what edits. You have some flexibility when it comes to your name. This can be useful if you want to separate work done on different computers for example.

### 3.4 Final notes

Working in the shell is not for everyone. It is recommended you use a GUI (like RStudio for R). These include:

-   GitKraken
-   GitHub Desktop

I won't go into these, since we won't be working much more in the shell.

***
## 4. Connecting RStudio to GitHub

Go back to your GitHub and [generate a "Personal Access Token"](https://github.com/settings/tokens) or PAT.\
Copy **AND SAVE** this code. This is now your password for Git.

Go in RStudio and install "gitcreds" or run the following script:


```r
install.packages("gitcreds")
gitcreds::gitcreds_set()
```

Enter your PAT.

Congrats! The hard part is over!\

You should now be able to push and pull from GitHub.

------------------------------------------------------------------------

## 5. Cloning a repository

### 5.1 The setup

Cloning essentially means copying what is currently in a GitHub repository onto your machine. We could do this in the shell, but let's not.

In RStudio, go to *File \> New Project \> Version Control \> Git*\
Now, copy this link and paste it as the "repository URL".\
"<https://github.com/Apps980/GitHub-RMarkdown-Tutorial.git>"\
Make a new folder for this project, the press "Create Project".

You should now have access to the repository I used for this tutorial.

### 5.2 The tools

This should have automatically pulled the files from the repository, but it's a good place to show you where things are in RStudio.\

![](./Figures/Where-Git-is-in-RStudio.png)

This is where you will find the tools related to using Git.\
Under this bar, you will find the buttons for pulling, pushing and committing.\

![](./Figures/Push-Pull-Commit-in-Rstudio.png)

>These buttons will be your bread and butter.

Let's make our first push and commit.

### 5.3 First steps

Pull from the repository and find the "README.md" file. Open it.\
Under checklist, add your name and whatever message you want to write. Save the file before you close it.

![](./Figures/Modified-File.png)

>Notice the blue "M" that appears next to the README file? Git detected a change.

Now, click on the box under "Staged" in line with the README, then press "Commit". A new box should open.

![](./Figures/Your-first-Commit-1.png)

>In green, you will have additions, in red, deletions.

Now, enter a commit message, commit, then push.

![](./Figures/Your-first-Commit-2.png)

>I predict only one of you will be successful.

For most of you, there will be an error! Oh no! Not to worry, this is one of the "joys" of collaborating in GitHub.\
**This is why you should be pulling and pushing regularly!**

The issue that happened here is that one person pushed a change, and others do not have that change (yet). To get around this, pull first, then commit and push. More importantly, communicate with your collaborators! Tell them when you are trying to push something so that someone else doesn't push at the same time. 

So once more, with passion! Try to pull, commit, and push. Reminder: it works best when you work as a team.

### 5.4 Let's double check

Go into the repository onto your browser. Check and see that your commit was sent to GitHub correctly.

Voila! You've made your first push and commit!

------------------------------------------------------------------------

## 6. Your first RMD script

### 6.1 The boilerplate script

Brilliant! We should all have successfully connected RStudio to the GitHub repository. Let's start our first RMD script.

Go to *File \> New File \> R Markdown*\
Give it a title, and your name. Check "Use current date when rendering document" and "HTML". Press "OK" to make a new file.

There will be some information written at the top. Don't touch that yet, that's your YAML header.

The rest of the document gives some examples on what you can do in RMD. Pay close attention to the highlighted sections. These are coding chunks.

![](./Figures/New-Markdown.png)

>The text in white under the coding chunk is regular text, like what you are reading now.

The changing the YAML header can be useful. I prefer to export my work in .md, a markdown file. In GitHub, it's more aesthetic than .Rmd, and miles better than HTML.\
Let's make our output a markdown file. Simply replace "html_document" with "github_document" in the header.

Let's see what the knitted document looks like. "Knitting" renders your document, showing you what your script will look like.\
To do this, press the "knit" button at the top of the script. You can change what document type it makes with the arrow. For now, just press "knit".

\
A preview should pop up.\

![](./Figures/Boilerplate-Script-1.png)

>Pretty cool, right?

It even outputs your plots!

![](./Figures/Boilerplate-script-2.png)

>Nifty! See how working with markdown makes showing off your script easier?

***
## 7 Formatting in RMD

Let's remove whats currently in the markdown script.

We can add titles and subtitles using headers: adding one or more "\#" before text will change the size of the heading. These headers will also appear in the right column of your script under "Outline", making it easier to go through your script.\
Try adding a couple headers, then knit the document again.

Now let's try some other text formats:


```r
*italics* 
**Bold** 
***Italics and Bold***
- Bullet points 
1. Ordered lists 
Superscript^2^ 
~~Strikethrough~~
$Formulas$
![](path to image)
[text](web link)
```

>Some of these require an empty line between bodies of text and, for example, a list.

That's a lot to take in, but there's a cheat sheet in the resources AND RStudio is kind enough to provide us with tools for easier formatting.\

![](./Figures/Visual.png)

>In the top left of the script, there's a "Source" and "Visual" button.

### 7.2.1 Visual mode

The source mode is your hard script. The visual mode let's you format your script in real time. Take some time to familiarize yourself with it.

***
## 8. Coding in RMD

Meat and potatoes. Why using RMD is awesome.

To make a code chunk, start by entering \`\`\` followed by "{r [chunk name]}". Close the chunk with another \`\`\`.\
Inside the brackets, give a name to your chunk. This will help you keep the chunks organized, and you can quickly switch between chunks using the button on the bottom left of the window.\
As with any R script, it is good nature to set your working directory and queue up the libraries you'll need. Your working directory is by default the main folder, but let's change it to Data and open the data file within it.

Run the following script:


```r
setwd("Data")
data<-read.csv("data.csv")
```

**This will only change the directory in this chunk** but your data will be imported into RStudio for you to use.


```r
summary(data)
```

```
##     Small.SD         Big.SD      
##  Min.   :4.500   Min.   : 0.000  
##  1st Qu.:4.925   1st Qu.: 4.625  
##  Median :5.000   Median : 5.000  
##  Mean   :5.000   Mean   : 5.000  
##  3rd Qu.:5.075   3rd Qu.: 5.375  
##  Max.   :5.500   Max.   :10.000
```

> This is an old dataset of mine from my undergraduate studies.

Take a moment and knit the document. See how it also spits out the code you entered? Let's change that.\

In the brackets preceding the chunk, add ", echo = F" after the chunk name and knit the document again.


```
##     Small.SD         Big.SD      
##  Min.   :4.500   Min.   : 0.000  
##  1st Qu.:4.925   1st Qu.: 4.625  
##  Median :5.000   Median : 5.000  
##  Mean   :5.000   Mean   : 5.000  
##  3rd Qu.:5.075   3rd Qu.: 5.375  
##  Max.   :5.500   Max.   :10.000
```

>No more code!

Now try ", include = F" and ", eval = F". There are many other options in the cheat sheet.

>If you're copy-pasting your chunk, be sure to change the name of the chunk.

Let's keep going. Let's manipulate the data and run some tests.


```r
Big.SD<-data$Big.SD
Small.SD<-data$Small.SD
```

Next, let's run some t-tests to find out if the mean equals 0.


```r
t.test(Small.SD, conf.level=0.95)
```


```r
t.test(Big.SD, conf.level=0.95)
```

>Where are my results?


```
## 
## 	One Sample t-test
## 
## data:  Small.SD
## t = 84.828, df = 14, p-value < 2.2e-16
## alternative hypothesis: true mean is not equal to 0
## 95 percent confidence interval:
##  4.87358 5.12642
## sample estimates:
## mean of x 
##         5
```

```
## 
## 	One Sample t-test
## 
## data:  Big.SD
## t = 8.9006, df = 14, p-value = 3.873e-07
## alternative hypothesis: true mean is not equal to 0
## 95 percent confidence interval:
##  3.795148 6.204852
## sample estimates:
## mean of x 
##         5
```

>Found them!

Lastly, let's plot our results.


```r
data.together<-cbind( Small.SD, Big.SD)
boxplot(data.together, boxwex=0.5, ylim=c(3.5, 6.5), col="Gray", medlwd=2, whisklty=1, staplewex=0.4)
```

![](GitHub-RMarkdown-Tutorial_files/figure-html/Plotting data-1.png)<!-- -->

>Won't you look at that... The Big SD dataset has a wider distribution than the Small SD dataset.

Let's make one final commit and push to the repository. I trust you've learned how.

Let's have a look at your markdowns. Open the .md file you created in the GitHub repository and have a look at it.

***
## 9. Creating a new repository
It's all fun and games working in my repository, but a fledgling must leave the nest and take to the skies. This involves making your own repository.

To do so, go back to GitHub and open your repositories.

![](./Figures/New-Repository.png)

Then press the green "New" button.\
Give a name to your new repository, a description, and a README file, then create the repository.

Lastly, copy the link to the repository from the green "<> Code" button.

> Make sure you use the "HTTPS" option

Then follow the instructions from 5. onwards.

**That's it! You know should know how to use GitHub and R Markdown!**

***
## 10. Resources
You should definitely check out [Happy Git with R](https://happygitwithr.com/index.html) for resources involving GitHub and R.

The [R Markdown CheatSheet](https://www.rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf) has everything you reasonably need to work in R Markdown.

When you have issues, [rubber duck debugging](https://en.wikipedia.org/wiki/Rubber_duck_debugging) is the way to go. Trust the ducky.

Lastly, I will make this tutorial available to everyone. Let me know if you'd like anything added to it.

***

