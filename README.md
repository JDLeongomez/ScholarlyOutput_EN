# ***ScholarlyOutput*** <img src="https://upload.wikimedia.org/wikipedia/commons/c/c7/Google_Scholar_logo.svg" align="right" width=100 height=100 alt=""/>
Plot your scholarly output using the [<code>scholar</code>](https://cran.r-project.org/web/packages/scholar/vignettes/scholar.html) R package 

<!-- badges: start -->
![](https://img.shields.io/github/last-commit/JDLeongomez/ScholarlyOutput)
[![License: MIT](https://img.shields.io/badge/License-GPL--3.0-yellow.svg)](https://github.com/JDLeongomez/ScholarlyOutput/blob/main/LICENSE)
[![DOI](https://zenodo.org/badge/536271372.svg)](https://zenodo.org/badge/latestdoi/536271372)
<!-- badges: end -->

**_ScholarlyOutput_** is a small R Shiny app for creating and exporting a complete plot of your academic [**Google Scholar**](https://scholar.google.com/) profile.

[![](https://img.shields.io/badge/Run%20the%20app-8A2BE2)](https://shiny.jdl-svr.lat/ScholarlyOutput/)

(**NOTA:** Para la versión en Español, entra a https://github.com/JDLeongomez/ScholarlyOutput_ES)

It only requires the full link to your Google Scholar profile (just copy it and paste it in the box), and it will create a plot with your name (as it appears on your Google Scholar profile) and two panels:

<ol type="A">
  <li><b>Citations per publication</b> including both your h-index and, importantly, <a href="https://en.wikipedia.org/wiki/G-index">g-index</a> (which I have never seen in plots before)</li>
  <li><b>Number of publications and citations per year</b> including total number of citations</li>
</ol>

Below is an example of the **_ScholarlyOutput_** UI showing a plot of my own profile:

![ScholarlyOutput user interface](img/ScholarlyOutput.jpg)

You can change an accent colour and filter publications.

![Colour picker](img/colour_picker.jpg)

Once you are happy, the plot can be exported to **PNG**, **PDF**, and even **SVG** format in case you want to edit it (the downloaded file will be named <code>Scholar_profile.png</code>, only changing the file extension depending in the format you selected).

The downloaded plot (in this case, as PNG) looks like this:

![ScholarlyOutput plot example](img/Scholar_profile.png)

This app uses the fantastic [<code>scholar</code>](https://cran.r-project.org/web/packages/scholar/vignettes/scholar.html) R package to extract the info from your Google Scholar profile, and then several packages (mostly [<code>tidyverse</code>](https://www.tidyverse.org/) packages including [<code>ggplot2</code>](https://ggplot2.tidyverse.org/)) to wrangle and plot these data.

## How to run it locally

While this app is available from my (rather slow) personal [Shiny server](https://shiny.jdl-svr.lat/ScholarlyOutput/), if that is too slow or my server is not working, you can always run it locally in your computer with R installed. 

To do this, you can simply run the code below in R:

```R
library(shiny)
runGitHub("ScholarlyOutput", "JDLeongomez")
```
Alternatively, you can always clone or [download](https://github.com/JDLeongomez/ScholarlyOutput/archive/refs/heads/main.zip) the **_ScholarlyOutput_** repository, and run the [<code>app.R</code>](https://github.com/JDLeongomez/ScholarlyOutput/blob/main/app.R) file.

<details>
  <summary><b>Click here to make sure you have all the necessary packages installed</b></summary>
<br>Please note that the <code>shiny</code> package must be installed. Other R packages used in this app include <code>thematic</code>, <code>shinythemes</code>, <code>colourpicker</code>, <code>stringr</code>, <code>scholar</code>, <code>dplyr</code>, <code>tidyr</code>, <code>ggplot2</code>, <code>ggpubr</code>, <code>scales</code>, and <code>purrr</code>.<br><br>

If you want, you can first run the following code, which will check which of these packages are already installed on your computer, and install the missing ones (if any).

```R
# Required packages
packages <- c("shiny", 
            "thematic", 
            "shinythemes", 
            "colourpicker", 
            "stringr", 
            "scholar", 
            "dplyr", 
            "tidyr", 
            "ggplot2", 
            "ggpubr", 
            "scales", 
            "purrr")
# Install packages not yet installed
installed_packages <- packages %in% rownames(installed.packages())
if (any(installed_packages == FALSE)) {
 install.packages(packages[!installed_packages])
}
```
</details>

## Why I made this super small app 

I originally wrote a script to download data from Google Scholar and make these plots for a particular version of my CV. However, several friends liked it and wanted to make plots of their own profiles (and be able to easily update them), so I decided to turn the code into a Shiny App for anyone to use.
