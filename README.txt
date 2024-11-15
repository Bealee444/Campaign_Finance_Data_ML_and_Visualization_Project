// DESCRIPTION //
Algorithm:
This part of the package creates a network, treating each unique donor/recipient pair as an edge and applying some filters detailed in our paper. Using a plot of the eigen-spectrum of the resulting adjacency matrix, we attempt to discover a hierarchical structure which informs a spectral fuzzy-c-means clustering of the nodes in the network. The resulting clusters can be sorted into parents and children using the final jaccard similarity comparisons.

Decision Tree:
This part of the package attempts to make sense of the outputs of the algorithm. We train a decision tree to predict cluster membership and take a look at its splitting criteria in order to understand the characteristics of our clusters.

Data transfer from Algorithm to Visualization:
This part of the package transfers the algorithm results to make them easily usable in the visualization. It merges the results from the algorithm with the original data set, mapping cluster assignments to the full data set. This allows us to inspect the characteristics in our data as well as create the json file needed as an input in our visualization. There are three files needed to transfer from algorithm results to usable data in our visualization: the raw data file, the algorithm results file, and the ToJson.ipynb file. Use the raw data file and the results from the clustering algorithm as inputs in the code ToJson.ipynb. To run a demo, run every cell in the jupyter notebook file to connect algorithm results to raw data. The final cell creates an output json file that interacts directly with the visualization. This python code is hard coded to evaluate based off of the hierarchy we selected to work with as a group, and would have to be modified for a new hierarchy. To run a demo make sure to use algorithm results that align with the hierarchy indicated in our final paper. 

Visualization:
We are using D3.js (version 3) which is a JavaScript library for producing dynamic, interactive data visualizations in web browsers. It's used extensively in this code for creating the sunburst chart and handling data binding, DOM manipulation, and transitions. We are also using basic HTML and CSS are used for structuring the webpage and styling the elements. CSS is used for styling the chart elements, such as colors, fonts, and layout.


// INSTALLATION //
Data:
All the data we used is freely available through an educational Open Secrets Bulk Data Account

Installation:
To run the clustering algorithm, you will need to install the following packages: numpy, scipy, pandas, networkx, fcmeans, and matplotlib

To run the decision tree code, you will additionally need to install scikit-learn

To install the packages, use the package manager pip:
pip install [insert package name]


// EXECUTION // 
To determine the number of clusters at each level, first run the split_alg.ipynb file up to the spectral characterization plot, and then use it to define the clusters in the next cell.
The rest of the algorithm should run without issue.

To explore the structure of the clusters, run the entire decision_tree file only ever altering the value of y, the labels that the decision tree is predicting

The visualization part of the package uses the sunburstdatafinal.json file to create an interactive sunburst visualization of our results on an html page called sunburst.html. We recommend running the visualization by setting up a HTTP server by typing python -m http.server 8000 into the command prompt after navigating to the directory containing the sunburstdatafinal.json file and the sunburst.html file, then opening at the web browser http://localhost:8000/.
