# machine_learning_project-unsupervised-learning

## Project Outcomes
- Unsupervised Learning: perform unsupervised learning techniques on a wholesale data dataset. The project involves four main parts: exploratory data analysis and pre-processing, KMeans clustering, hierarchical clustering, and PCA.

### Project Description: ###
In this project, we will apply unsupervised learning techniques to a real-world data set and use data visualization tools to communicate the insights gained from the analysis.

The data set for this project is the "Wholesale Data" dataset containing information about various products sold by a grocery store.
### Project Description: ###
In this project, we will apply unsupervised learning techniques to a real-world data set and use data visualization tools to communicate the insights gained from the analysis. The data set for this project is the "Wholesale Data" dataset containing information about various products sold by a grocery store.

The project will involve the following tasks:

-	Exploratory data analysis and pre-processing: We will import and clean the data sets, analyze and visualize the relationships between the different variables, handle missing values and outliers, and perform feature engineering as needed.
-	Unsupervised learning: We will use the Wholesale Data dataset to perform k-means clustering, hierarchical clustering, and principal component analysis (PCA) to identify patterns and group similar data points together. We will determine the optimal number of clusters and communicate the insights gained through data visualization.
  
### Exploratory data analysis and pre-processing: ###
We will import and clean the data sets, analyze and visualize the relationships between the different variables, handle missing values and outliers, and perform feature engineering as needed.
Findings:
- There were no empty records in the data, only a slight spelling error in one of the columns which was presumed to be Delicatessen or Deli instead of "Delicassen" as the other columns of the dataset were categories of foodstuffs, groceries or other consumable household item. Renamed it to 'Deli'
- Boxplots were made to establish ranges and find any outliers, of which there were quite a few in most categories. However, at first I kept them in, because the unsupervised nature of this task means that we don't yet know if those outliers will have some significance that isn't obvious from box plots.
- The two columns that did not appear to reference categories of consumables were Channel and Region. These make sense in a wholesale commerce context as Channel being different means by which goods were purchased (e.g. online or instore), and the region being different locations. My immediate guess was that the data may be divisable by channel as behaviour for buying e.g. Frozen goods may be different from buying Paper or Detergents
- I ran a Seaborn heat map and found significant correlations between channel and some of the item categories, but very little to no correlation between region. The items that correlated with the same channel (Fresh, Frozen and Deli) also correlated with one another quite strongly. Because of this, my initial guess for the number of clusters was very much along channel lines, that there would be two channels and therefore two clusters of data.

### Unsupervised Learning: ###
We will use the Wholesale Data dataset to perform k-means clustering, hierarchical clustering, and principal component analysis (PCA) to identify patterns and group similar data points together. We will determine the optimal number of clusters and communicate the insights gained through data visualization.
Findings:
- **K Means:** Because of the very weak behaviour of region correlating with nothing, I ran three separate clustering experiments: one with region removed; one with channel removed and one with both retained. The results for the number of clusters was inconclusive but centred around 2 or 3 clusters being most appropriate
- **Hierarchical Clustering:** This method revealed that there is a very marginal increase in value for running with 3 clusters. Of 430 data points, only 6 were labelled in this 3rd cluster if we modelled with a 3rd cluster instead of only 2. This built the evidence that 2 clusters was the best model, putting 2 ahead of the argument for 3 clusters.
- **PCA:** PCA created Principal Components where PC1 and PC2 account for 61% of variability. This is not bad but it does leave a significant amount of variability unaccounted for. If 3 PCs is specified, then PC3 accounts for only a 12% further explanation of the variability in the data. For different reasons, this 3rd Principal Component and the 3rd cluster of the clustering models both feel 'shoe-horned' in with marginal evidence helping their case.

### Overall Conclusion ###

This project looked at some exploratory analysis of a wholesale sales dataset. It identified a column which describes two 'channels' of wholesale commerce and strong correlations between channels and specific types of goods, which makes good sense in the commerce domain as some goods are perishable which may cause the channel by which they are purchased to be different on average than pantry or other nonperishable goods. This domain knowledge and the correlation matrix took me down the path of likely 2 or perhaps 3 clusters of data.

The evidence strengthened for 2 clusters from the clustering models as explained above in the Unsupervised Learning section. When combining with PCA results, which are skewed by outlier data, it becomes apparent that the 3rd principal component and likely the data points of the 3rd cluster are being impacted by the outliers that we intentionally did not remove from the dataset. PCA is known to be sensitive to outliers, of which there are many in this dataset, and without them there I am quite confident the explanation of variability for PC3 would be much lower, and the case for 3 clusters would also be scant.

**Next Steps** We should re-run this again with outliers removed, there were quite a lot of them in the Fresh category/column. The explanation of variability for PC3 would decrease and the 3rd cluster may no longer be viable at all, and we would be left with a solid conclusion of two clusters likely accounting for the two channels of sales.
