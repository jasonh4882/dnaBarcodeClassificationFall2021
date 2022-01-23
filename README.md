# DNA Barcode Identification using K-mer Based Feature Engineering

## Description

The goal of this project was to take in a DNA barcode and then make a classification as to what species the sample belongs. There are some species in the test data that are "new species" not seen in the training data. Such a sample should be classified with a label of -1. This was done as a part of a Kaggle competition that can be found [here](https://www.kaggle.com/c/dna-barcode-classification/overview).

As a part of the competition, 4 files were provided: a sample submission CSV, test features CSV, train features CSV, and train labels CSV. The training features and corresponding labels were to be used as the basis for editmating the test label for each set of test features. 

The primary method used in this project to identify the test labels was k-mer based feature engineering combined with a random forest. This was accomplished using the Python programming language primarily inside JupyterLab notebooks. 

### Competition Results

In total, only one submission was made. This was primarily due to the time investment that this one submission took. Since there was only one to choose from, this submission was used for both the public and private leaderboards. A breakdown of the methods to generate this submission can be found the [methodWriteup.md](/methodWriteup.md) file.
    
***NOTE**: For clarification, Kaggle has two leaderboards. The public one can be seen at any time while the private one can only be seen after the competition is over. The private leaderboard also only allows two submissions to be counted. The leaderboards are each based on only around half of the whole dataset. This allows for feedback on the approximate preformance of a model without revealing the data that will actually be tested against. This discourages manual edits of a submission and other inproper submission methods*
    
#### Comparitive Performance ####

Compared to the other submissions made by all teams, the best model submitted by Jason Hampshire:

- **Public Leaderboard**: An accuracy of **96.749%** did **5th** best on the public board. Submissions by [Xuan Zhang](https://www.kaggle.com/xuanzhang8), [Yunyi Li](https://www.kaggle.com/yunyili315), [Stuart Livingston](https://www.kaggle.com/stuartlivingston), and [Yanling Pan](https://www.kaggle.com/giraffecolor) achieved a higher accuracy of **96.797%**, **97.230%**, **97.447%**, and **97.495%** respectively with Yanling Pan being the most accurate. This placed the submission on the **71st percentile**

*Complete public leaderboard CSV can be found [here](/dna-barcode-classification-publicleaderboard.csv)*

- **Private Leaderboard**: An accuracy of **96.677%** did **4th** best on the private board, moving up one position from that of the public board. Submissions by [Yunyi Li](https://www.kaggle.com/yunyili315), [Yanling Pan](https://www.kaggle.com/giraffecolor), and [Stuart Livingston](https://www.kaggle.com/stuartlivingston) achieved a higher accuracy of **96.797%**, **97.664%**, and **97.664%** respectively. Outside the range of significant digits  by the leaderboard, Stuart Livingston was the most accurate by less than one thousanth of a percent. While the private did not do as well as the public in terms of raw score, the submission still did well compared to other scores. The submission fell on the **76th percentile** of all submissions.

The top 10 private percentage scores were the following *(accuracy between 0 and 1)*:

1. **Stuart Livingston** *(Leaderboard Tie)*
    - *Accuracy*: 0.97664
1. **Yanling Pan** *(Leaderboard Tie)*
    - *Accuracy*: 0.97664
1. **Yunyi Li**
    - *Accuracy*: 0.96797
1. ***Jason Hampshire***
    - *Accuracy*: 0.96677
1. **Xuan Zhang**
    - *Accuracy*: 0.96508
1. **Yousif Hag Ahmed**
    - *Accuracy*: 0.96412
1. **Danie6846435l**
    - *Accuracy*: 0.96099
1. **Isaac Manring** *(Leaderboard Tie)*
    - *Accuracy*: 0.95978
1. **Niloy Talukder** *(Leaderboard Tie)*
    - *Accuracy*: 0.95978
1. **Alexander Phillips**
    - *Accuracy*: 0.95738

*Complete private leaderboard can be found [here](https://www.kaggle.com/c/dna-barcode-classification/leaderboard)*
    
## Software

Python and JupyterLab notebooks were used for all feature and submission creation.

## Installation

1. Download and install [Python](https://www.python.org/downloads/) version 3.9.7 or later
1. Install [JupyterLab](https://jupyter.org/install) using a Python Package manager, such as [pip](https://pypi.org/project/pip/).
1. Launch JupyterLab by calling `Jupyter lab` in a terminal while in the directory that the package was installed into.
1. Open *comp2.ipynb* for the notebook that was used for all of the initial setup and pre-generation work.
1. Open *comp3.py*, *comp3.py*, or *comp3.py* for the scripts that generated the feature sets.
1. Open *comp6.ipynb* for the notebook that was used to take the generated feature sets, create a Random Forest model, and predict the labels.

***NOTE**: Any and all packages that are used in any of the scripts, both .py and .ipynb **must** be downloaded and installed first before running the dependant files.*

***NOTE**: All .py files **must** be run from a cmd.exe terminal, not inside of the JupyterLab notebook environment. Run these scripts inside a terminal by calling `py comp#.py` where `#` is the desired script number while also being inside the same directory as said script.*



## Roadmap

The sole purpose of this project was for the Kaggle competition. 
Now that the competition is over, there is no reason to continue work on this project.

## Authors & Acknowledgments

- All code models and scripts were written and generated by Jason Hampshire.
- Thanks to George Mohler for hosting the competition as a part of IUPUI's CSCI 49000 class in Fall of 2021.

## Project Status

This project is **Completed** and will see no further work.