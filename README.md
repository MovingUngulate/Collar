# Collar

## Overview

This package aids in easily downloading GPS collar datasets, and associated data, that reside online (satellite linked collars).

## Installation

### Currently, the only version of part is on GitHub:

To install:

```{r}
install.packages("devtools")

devtools::install_github("MovingUngulates/Collar")
```

To uninstall current version and get newest version:

```{r}
remove.packages("Part", lib="~/R/win-library/3.4")

devtools::install_github('MovingUngulate/Collar')
```

## General Thoughts
Currently, there are methods for ATS (global star and Iridium), SirTrack and Vectronics.
The current methods are simply based on systems that I've had access to over the years. If
you'd like to add your system please contact me about adding it! Adding new functionality
is hoped for but will require partnership and access to your specific sites to determine
how to automate your workflow.

## Usage

ATS Downloads

```{r}

examp<-ColDownload(username = ATSUser,password=ATSPass,
                        dirdown = tempdir,cType='ATS/IRID')

```

SirTrack Downloads
To get yourlink, login to your SirTrack site, right click the download entire dataset csv
link and copy link address. Paste into the function as a character vector. Should only 
need to do once.

```{r}

examp<-SirTrackDat(user = ATSUser,pass=ATSPass,
                        saveas = 'C:/Users/mhayes1/Desktop/STDat.csv'
                        ,yourlink=seehelp)

```

Vectronic Downloads

```{r}

#Ensure that your data is saved as .csv in GPSPlusX!
examp<-getVec('GPSPlusxpath')

```

Mixture of some ATS, Vectronic and SirTrack Data (if you don't have one or two that ok!)

```{r}

#vecpath is the character path to your vectronic download folder (.csv!)
#ATSUsers/ATSPass is the character string of ATS Usernames/Passwords (can do #c('acct1','acct2') if you have more than one!)
#tempdir is a temporary storage folder
#ST is TRUE/FALSE if you have sirtrack data
#If ST == TRUE, STUser and STPass are the username/password for sirtrack site
#yourlink is the yourlink described above

examp<- CombDat(vecpath,ATSUsers,ATSPass,
               tempdir=tempdir,ST,STUser,STPass,yourlink)
```