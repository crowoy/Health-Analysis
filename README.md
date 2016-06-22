# Health-Analysis
Tool for visualising and analysing personal fitness data.

The tools for displaying data from the Jawbone fitness trackers is great, and very intuitive. However, I wanted to create a tool to analyse the raw data in greater depth.

Thankfully, Jawbone allows you to download all of your raw data at the click of a button on their website, which includes your data over `78` tracked features.

### Normalising the Data

Upon importing the data and plotting it, the range of values was too large (e.g. some days I would walk 2k steps and some 40k steps). Therefore, normalising was the obviously solution.

### Dimensionality Reduction

As Jawbone tracks you on `78` features, it is extremely difficult to gather interesting conclusions or trends from this. Therefore some dimensionality reduction must take place.

**The Null Values**

Fitness data gathered from these wearable, etc is largely incomplete. For example, when you take off your fitness tracker (e.g. to charge it), the data is populated with null values, however certain features, such as steps, weight, BMR, etc may still be populated with values (they either remain constant or can be tracked without your tracker, such as steps with your phone).

Furthermore, many of the features require user input (such as weight, calories consumed, caffeine consumed, etc). The vast majority of these features are therefore also populated with null values (as most users don't other inputting these).

Therefore, the first step in reducing dimensions was getting rid of all of these values.

**The Constant Values**

It was rapidly discovered that a lot of the data was features populated with the constant values over time. For example, if you only inputted your weight once, then it would remain constant. This data is very uninteresting. I removed this.

**Extracting Interesting Features (PCA)**

So, now we are left we all 'potentially' useful data. However, again many of these features are pretty useless and carry little interesting value. In order to further reduce the dimensions of the data, I carried out some Principal Component Analysis (PCA).

This was relatively easy once planned out on paper, and I initially implemented it when only looking at `4` features in order to make things more manageable. First, I would find the covariance matrix between all the features. Then find the eignvalues and corresponding eigenvectors for the covariance matrix, and rank the features according to the eignvalues. I took these eigenvalues as my effecive measure for how interesting each feature was going to be.

From here, you can change the value of `n` at the top of the file and it will automatically do everything. Here is the plots of the top `6` features from my data:

![6 Feature Plot](https://raw.githubusercontent.com/crowoy/Health-Analysis/master/res/6-feature-plot.png)

### Dependencies
- Python
- Jupyter Notebook
- Jawbone Data

### How-to
- Install dependencies
- Download/clone this repository
- Move the download into its own folder (e.g. `/Health/Analysis`)
- Create a separate data folder (e.g. `/Health/Data`) and place your Jawbone data in here
- Now run Jupyter and open the notebook and run the program!
