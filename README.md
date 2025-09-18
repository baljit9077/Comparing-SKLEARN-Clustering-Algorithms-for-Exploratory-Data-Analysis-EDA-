# Comparing-SKLEARN-Clustering-Algorithms-for-Exploratory-Data-Analysis-EDA-
TASK 1: Preparing the test Environment:

A. Evidence of Loading the 'data.npy' data file.
 
Here in screen shot it showing the proof that the data file is loaded in Google Colab and showing the number of instances (510) and features (2).
B. Scatter plot the 'data.npy' data.
 
C. Annotating various group of data.

 
D. plotting the results for each of the algorithms:
MiniBatchKMeans
 
MeanShift
 



HDBSCAN
 
Agglomerative Clustering
 

TASK 2: Choosing each algorithm's parameters values
Algorithm Name	args or kwds used	Args or kwds values	Justification
MiniBatchKMeans	'n_clusters'
	     4
	


	  'init'
	'k-means++'
	The 'k-means++' method is generally preferred due to its ability to enhance the quality of the initial clusters and accelerate convergence(snowflake.ml.modeling.cluster.MiniBatchKMeans | Snowflake Documentation).
	'batch_size'
	    100
	Separating a dataset into batches can drastically decrease work and accelerate the growth speed of clustering algorithms (Efficient algorithm for big data clustering on single machine). Batch size 100, By selecting this value, memory is not over-loading, thus ensuring efficient updates and reliable perfor-mance (Purdom).
	'max_iter'	    300
	The max_iter option is used to control the number of iterations the algorithm goes through before stopping (Xu, Z., Lu, Y. et al).

Algorithm Name	args or kwds used	args or kwds values	Justification
MeanShift	'bandwidth'
	 estimate_
bandwidth
	Scikit-learn's estimate_bandwidth() function is a useful tool for automatically selecting an ap-propriate bandwidth size based on your data. This enhances the functionality of the Mean Shift algorithm by adjusting to the unique pat-tern of data(webmaster).
The most critical parameter is bandwidth. It indicates the radius of the area in the feature space that will be considered when computing the mean shift (Yenigün, Practical Guide to Mean Shift Clustering).
	'bin_seeding'
	True
	The algorithm is expedited by decreasing the quantity of initial seeds. An increase in pro-cessing speed is achieved by binning the initial kernel locations onto a grid that corresponds to the bandwidth and it also reduce the cluster took time (snowflake.ml.modeling).

Algorithm Name	args or kwds used	args or kwds values	Justification
HDBSCAN	'min_cluster_size'
	  60
	By merging smaller clusters into larger ones, the num-ber of clusters can be reduced by increasing the value of min_cluster_size. For instance, the setting of min_cluster_size to 40 will endeavour to merge smaller clusters into larger clusters. The value may ultimately merge all clusters into a single cluster if it is set even higher (Parameter Selection for HDBSCAN* — hdbscan 0.8.1 documentation). As this parameter increases, the final number of clustering species will decrease, and fewer points than this will be regarded as noise. Which assist in determining the minimum sample size in a neighbourhood and the smallest size of clusters to con-sider a point as a core point (Ship AIS trajectory cluster-ing).
	'min_samples'
	10
	Which determines the minimum number of samples in a neighbourhood for a point to be classified as a core point. Clustering becomes more conservative as min_samples increase, as it treats a greater number of points as noise and only forms clusters in denser re-gions. In contrast, the clustering process becomes less conservative as min_samples decrease, resulting in the inclusion of a greater number of points in clusters but an increased risk of identifying spurious clusters (Ship AIS trajectory clustering).
	'cluster_selection_epsilon'
	0.8	The cluster_selection_epsilon parameter in HDBSCAN assists the merging of clusters that are closely located. Many of the clusters have been merged into larger clus-ters when cluster_selection_epsilon is set to 0.8. Con-sequently, the output now displays a reduced number of clusters with larger sizes and what was previously identi-fied as distinct clusters (Evaluation of Density-Based Spatial Clustering for Identifying Genomic Loci Associat-ed with Ischemic Stroke in Genome-Wide Data). 
	'metric'
	'euclidean'	Compared to alternative distance measures, the cluster-ing algorithms that use the Euclidean distance metric achieve superior cluster separation (Im-pact_of_Distance).
	'cluster_selection_method'	'leaf'
	This method prevents the formation of one or two large clusters with numerous small clusters. Rather, it tends to generate a greater number of small, which may in-clude variable density clusters. This method concen-trates on the selection of leaf nodes, which leads to the formation of numerous small, homogeneous clusters. It is especially beneficial when users prefer clusters that are small and have a more consistent internal structure (Parameter Selection for HDBSCAN* — hdbscan 0.8.1 documentation).


Algorithm Neame	args or kwds used	args or kwds values	Justification
Agglomerative Clustering	'n_clusters'
	   4
	Because it is logical that there should be 4 cluster in this data set.
	'linkage'
	'single'
	Single linkage is a fast algorithm that can perform well on non-globular data however, it performs poorly in the presence of noise (Comparing different hierarchical linkage methods on toy datasets).
The single-linkage approach produced more compact and central nuclei, making these clusters more significant than those discovered by Ward's method (Tokuda, E.K.,et al).
	'linkage'
	'ward'
	Ward minimize variance within clusters and maximize distance between clusters, which works well for bimodal distributions but may create false clusters in unimodal distributions and fail to detect outliers (Tokuda, E.K.,et al). 














TASK 3: Testing and documenting the output of the algorithms
1.	MiniBatchKMeans
	'n_clusters':4 
¬¬¬ 
	'batch_size': 100
 

	'max_iter': 300 
 
2.	MeanShift
	'bandwidth':bandwidth
 
	'bin_seeding':True
 
3.	HDBSCAN
	'min_cluster_size':60
 

	'min_samples':10
 


	'cluster_selection_epsilon':0.8
 


	'cluster_selection_method':'leaf'
 
	'metric':'euclidean'
 





4.	Agglomerative Clustering
	'n_clusters':4
 
	'n_clusters':4,'linkage':'single'
 


  



	'n_clusters':4,'linkage':'ward'
 

TASK 4: Writing a short technical report analysing the “Clustering Results” 
a. Scatter Plot Clustering Results 
MiniBatchKMeans
	'n_clusters':4
This results in fewer, larger clusters, as the number of clusters is reduced to 4. It appears that certain clusters have merged in comparison to the previous one, which contained a greater number of distinct groups. In general, the clusters are spherical; however, they are larger and contain a greater number of data points. Whereas there are some anomalies: Yellow Cluster: This cluster contains a single data point from the orange cluster Red Cluster: The red cluster contains a small number of data points from the green and purple clusters. These anomalies indicate that, despite the algorithm's ability to identify distinct clusters, there are certain edge cases in which data points are not accurately assigned to their nearest cluster. Due to reasons of Cluster Boundaries, Initialization Sensitivity, Inherent Data Overlap.
	'batch_size': 100
The batch_size parameter has resulted in significant variations: In comparison to the without using parameter algorithm, the clusters appear to be less distinct. It appears that certain clusters have merged or shifted positions, suggesting that the change in batch size has had an impact. The clusters' distribution and positioning have altered, even though these are generally spherical. Displays distinct clusters, but with some misclassifications. The single data points from one cluster are displayed in another cluster. The misclassified points suggest that the algorithm's capacity to maintain precise cluster boundaries may be impacted by the increase in batch size. 
	'max_iter': 300 
Except for the circular cluster, which comprises five sub-clusters which are not spherical but rest of clusters are spherical, the plot displays distinct and distinct clusters. The precision of the clustering is improved by the increased iterations, as the clusters are well-separated and there are no significant misclassifications or outliers.

MeanShift
	'bandwidth':bandwidth
The plot displays the same two distinct clusters as in algorithm without parameter. The data points are similarly organized into a larger central cluster and a smaller upper cluster. The non-spherical shapes of the clusters are preserved. There are two clusters in total, but a few data points from the upper cluster are overlapping in the lower cluster. No substantial outliers are discernible in the plot.

	'bin_seeding':True
The plot displays the same two distinct clusters as in algorithm without parameter. The data points are similarly organized into a larger central cluster and a smaller upper cluster. The non-spherical shapes of the clusters are preserved. There are no noteworthy anomalies.

HDBSCAN

	'min_cluster_size':60
The plot displays clusters that are larger and fewer in number that is 2. Numerous points are classi-fied as noise (black points), suggesting a more stringent clustering criterion. The rise in black points indicates that a greater number of data points are regarded as noise. indicating a more stringent clus-tering criterion that decreases the granularity of the clustering outcome.
	'min_samples':10
Similar to the cluster with default parameter, the plot displays the same unique clusters, but with a greater number of points identified as noise (black points). The presence of a greater number of black points scattered around the clusters suggests an increase in the number of noise points. min_samples=10: The same clusters are observed, but a greater number of points are classified as noise. This more stringent criterion for cluster formation results in the exclusion of a greater number of points from clusters, which could potentially result in the loss of some of the finer details of the da-ta structure and an increase in the number of noise points.

	'cluster_selection_epsilon':0.8
This modification has a substantial effect on the clustering outcome by merging clusters that are more closely spaced. The number of clusters is reduced, with the data points mainly grouped into two larger clusters. This merging effect results in fewer, more inclusive clusters than the default settings.

	'cluster_selection_method':'leaf'
It has a major impact on the clustering outcome by generating a greater number of smaller clusters. The outcome is a clustering structure that is more splintered, with numerous data points forming small, distinct clusters. As a result, the algorithm is more susceptible to minor variations in data densi-ty and structure, as evidenced by the substantial increase in the number of points classified as noise (black points). Although this method can reveal finer details within the data due to the higher granular-ity of clustering, it also introduces more noise points, which may obscure the broader patterns. When the objective is to identify smaller, more detailed groupings within the data, this method is especially beneficial. 


	'metric':'euclidean'
The algorithm identified the same distinct clusters as in the default configuration which are consistent with the anticipated natural groupings. The presence of a noise point, as evidenced by the resulting scatter plot. Furthermore, the number of noise points (black) remains consistent with that of the cluster without parameter.


Agglomerative Clustering

	'n_clusters':4
The clustering outcome is significantly influenced by this adjustment, which provides a more detailed and granular separation of the data. The scatter plot that results demonstrates four distinct clusters. But the allocation of clusters is not optimal, as there are instances where two clusters overlap and merge together. In comparison to the broader clusters that are observed with the default settings, these clusters are more specific and defined. 

	'n_clusters':4,'linkage':'single'
The linkage is set to ‘single', and the number of clusters is set to 4. The clustering outcome is signifi-cantly influenced by these parameter adjustments, which alter the method by which clusters are merged and increase the number of clusters. The scatter plot that results displays four distinct clus-ters, as opposed to the two broader clusters that were observed with the default settings. This in-crease in the number of clusters results in a more detailed and granular separation of the data, which is more consistent with the expectation of multiple natural groupings.


	'n_clusters':4,'linkage':'ward'
	The linkage is set to 'ward', and the number of clusters is set to 4. The clustering outcome is significantly influenced by these parameter adjustments, which alter the method by which clusters are merged and increase the number of clusters. The scatter plot that results dis-plays four distinct cluster, as opposed to the two broader clusters that were observed with the default settings.
The 'ward' method merges clusters in a manner that minimizes the total within-cluster vari-ance, resulting in clusters that are uniformly distributed and cohesive. The more defined and separated clusters are indicative of this, as opposed to the more irregular and merged clus-ters.


b. The Intra-cluster versus inter-cluster distance among the clustering results.
MiniBatchKMeans
	'n_clusters':4

Intra-cluster Distance:The upper cluster is distinguished by its increased intra-cluster distance, which is because its points are more widely dispersed within the cluster. In the same vein, the dis-tances between the data points of the other three clusters are also greater.
Inter-cluster Distance:The separation between the lower clusters is minimal due to the negligible gaps between the differently coloured clusters.


	'batch_size': 100
Intra-cluster Distance:The orange, cyan, pink, and green clusters exhibit low intra-cluster distances, which suggests that these clusters are highly cohered and similar. The slightly higher intra-cluster distances of the yellow and blue clusters indicate that the data points within those clusters are more evenly distributed.
Inter-cluster Distance:The clusters are clearly distinguished and isolated from one another due to the high inter-cluster distance. This distinct separation facilitates the differentiation of various clusters and improves the overall quality and clarity of the clustering.

	'max_iter': 300 
	Intra-cluster Distance: The high cohesion and similarity within the upper 2 and centre clusters are suggested by the low intra-cluster distances. The intra-cluster distances of the purple and pink clusters are slightly higher, whereas the cyan, green, and blue clusters maintain reasonable cohesion.
Inter-cluster Distance:High inter-cluster distance seen on the upper 2 and centre clusters, are well-separated, whereas there are less inter distance seen in the clusters.
MeanShift
	'bandwidth':bandwidth
Intra-cluster Distance:  The upper cluster's lower intra-cluster distance suggests that it has a high degree of cohesion and similarity. The intra-cluster distance of the upper cluster is higher, indicating that the points within it are more dispersed, even though it is still relatively cohesive. 

Inter-cluster Distance: The clusters are clearly distinct and separated, indicating effective identifica-tion and separation of different groupings within the data. This enhances the overall clarity and quali-ty. The inter-cluster distance is notably high.
	'bin_seeding':True
Intra-cluster Distance: upper clusters these are highly cohesive and has a low intra-cluster distance, and cyan clusters these are moderately cohesive and has a slightly higher intra-cluster distance.
Inter-cluster Distance: Both clusters are clearly separated, with a high inter-cluster distance.
HDBSCAN

	'min_cluster_size':60
Intra-cluster Distance: Moderate cohesion is indicated by a highly cohesive upper cluster with a low intra-cluster distance and a more dispersed lower cluster with a higher intra-cluster distance. Fur-thermore, a significant number of points are designated as "noise" (black), which suggests that they do not adequately correspond to any cluster.
Inter-cluster Distance: The clusters are clearly separated, with a high inter-cluster distance.

	'min_samples':10
Intra-cluster Distance: The clusters all demonstrate low intra-cluster distances, which suggests that each cluster is highly cohered and similar.
Inter-cluster Distance: The clusters are clearly separated, with a high inter-cluster distance.

	'cluster_selection_epsilon':0.8
Intra-cluster Distance: A highly cohesive cyan cluster with a low intra-cluster distance, which sug-gests a high degree of similarity and compactness within the cluster, and a more dispersed yellow cluster with a higher intra-cluster distance, which reflects moderate cohesion among its data points.
Inter-cluster Distance: There is a clear and distinct separation between the cyan and yellow clus-ters, as evidenced by the high inter-cluster distance.

	'cluster_selection_method':'leaf'
Intra-cluster Distance: These clusters are highly cohesive, with low intra-cluster distances, suggest-ing a high degree of similarity and compactness.
Inter-cluster Distance: Cluster separation is evident and distinct, as evidenced by the clusters' dis-tinct colours and high inter-cluster distance. 

	'metric':'euclidean'
Intra-cluster Distance: Indicating high cohesion and similarity within each cluster, the clusters all exhibit low intra-cluster distances. 
Inter-cluster Distance: The clusters are clearly separated, with a high inter-cluster distance. 


Agglomerative Clustering

	'n_clusters':4
Intra-cluster Distance: Low intra-cluster distances suggest that each cluster is compact, suggesting that there is a high degree of cohesion and similarity within it. This indicates that the points within each cluster are densely packed, which is indicative of the effective grouping of similar data points.
Inter-cluster Distance: The four clusters are clearly separated, with a high inter-cluster distance. 


	'n_clusters':4,'linkage':'single'
Intra-cluster Distance: Each cluster, particularly the red and cyan clusters, appears to be compact, suggesting that there is high cohesion within these clusters and low intra-cluster distances. 
Inter-cluster Distance:
With a clear and distinct separation between the four clusters, the inter-cluster distance is high.
	'n_clusters':4,'linkage':'ward'
Intra-cluster Distance: The high cohesion and similarity within each cluster are indicated by the low intra-cluster distances. Additionally, each cluster is compact. 
Inter-cluster Distance: The four clusters are clearly separated, with a high inter-cluster distance. The clusters are clearly distinguished from one another.

c. Nominate the best clustering model for each algorithm.
MiniBatchKMeans
The third plot, which contains the parameters {'max_iter': 300}, is the optimal clustering model for MiniBatchKMeans.
High cohesion and similarity within each cluster are suggested by the compactness of the clusters and the low intra-cluster distances. The clusters are well-separated, with high inter-cluster distances, ensuring that they are distinct and non-overlapping.
Compared to the four-cluster solution, the six clusters offer a more detailed segmentation of the data. 


MeanShift
Nominated Model: The clustering results are nearly identical between the two configurations (bin_seeding=True and bandwidth=bandwidth), making it challenging to identify the optimal model. Two distinct and well-separated clusters with comparable compactness and cohesion are generated by both models.

HDBSCAN
The second plot with the parameters {'metric':'euclidean'is the optimal clustering model for HDB-SCAN.
Several clusters with distinct red, cyan, yellow, and purple clusters are generated by this configura-tion. The noise points are present, but they are significantly reduced in comparison to other configura-tions. The clusters are well-separated and compact.


Agglomerative Clustering
For Agglomerative Clustering, the second plot with the parameters {'n_clusters': 4, 'linkage':'single'} is the optimal clustering model.
Clusters that are compact and have low intra-cluster distances are generated in this configuration. Ensuring distinct and non-overlapping clusters, the clusters are well-separated with high inter-cluster distances.This dataset exhibits well-defined and distinct clusters, despite the fact that the'single' link-age method has a propensity to generate elongated clusters. This suggests that the clustering pro-cess is effective.


d. Compare the nominated model’s scatter-plotted
The most effective clustering algorithm for this task is Agglomerative Clustering, as determined by the visual comparison and performance analysis of the clustering results from MiniBatchKMeans, HDB-SCAN, and Agglomerative Clustering. The following factors are considered when drawing this conclu-sion:

Cluster Definition: Agglomerative Clustering generates clusters that are compact and well-separated, which are consistent with the desired number of clusters and the data's inherent structure.
Separation: The data is clearly interpreted due to the well-defined boundaries and minimal overlap of the clusters that have been formed.
Efficiency: The algorithm is appropriate for this dataset due to its ability to perform the clustering task efficiently.
Clarity: The clusters that emerge from Agglomerative Clustering are clear and distinct, accurately rep-resenting the data's inherent groupings.
Although MiniBatchKMeans and HDBSCAN also demonstrate satisfactory performance, Agglomera-tive Clustering provides the optimal equilibrium between efficiency, clarity, and cluster definition for this clustering task.

REFERENCES

•	snowflake.ml.modeling.cluster.MiniBatchKMeans | Snowflake Documentation. (no date). docs.snowflake.com. Available from https://docs.snowflake.com/en/developer-guide/snowpark-ml/reference/1.0.9/api/modeling/snowflake.ml.modeling.cluster.MiniBatchKMeans [Accessed 15 July 2024].
•	Alguliyev, R.M., Aliguliyev, R.M. and Sukhostat, L.V., 2020. Efficient algorithm for big data clustering on single machine. CAAI Transactions on Intelligence Technology, 5(1), pp.9-14.

•	Purdom, Y.N., Davide Risso, Stephanie Hicks, and Elizabeth. (no date). An introduction to mbkmeans. www.bioconductor.org. Available from https://www.bioconductor.org/packages/release/bioc/vignettes/mbkmeans/inst/doc/Vignette.html#batch-size [Accessed 16 July 2024].
•	Yenigün, O. (2023). Practical Guide to Mean Shift Clustering. Medium. Available from https://blog.devgenius.io/practical-guide-to-mean-shift-clustering-5fec0277e44b.
•	Parameter Selection for HDBSCAN* — hdbscan 0.8.1 documentation. (no date). hdb-scan.readthedocs.io. Available from https://hdbscan.readthedocs.io/en/latest/parameter_selection.html#selecting-min-cluster-size.
•	Wang, L., Chen, P., Chen, L. and Mou, J., 2021. Ship AIS trajectory clustering: An HDB-SCAN-based approach. Journal of Marine Science and Engineering, 9(6), p.566.
•	Khvorykh, G.V., Sapozhnikov, N.A., Limborska, S.A. and Khrunin, A.V., 2023. Evaluation of Density-Based Spatial Clustering for Identifying Genomic Loci Associated with Ischemic Stroke in Genome-Wide Data. International Journal of Molecular Sciences, 24(20), p.15355.
•	webmaster. (2024). Main Shift Clustering in Machine Learning with scikit-learn. Meccanismo Complesso. Available from https://www.meccanismocomplesso.org/en/main-shift-clustering-in-machine-learning-with-scikit-learn/ [Accessed 22 July 2024].
•	Comparing different hierarchical linkage methods on toy datasets. (no date). scikit-learn. Available from https://scikit-learn.org/stable/auto_examples/cluster/plot_linkage_comparison.html.
•	Tokuda, E.K., Comin, C.H. and Costa, L.D.F., 2022. Revisiting agglomerative cluster-ing. Physica A: Statistical mechanics and its applications, 585, p.126433.

•	Xu, Z., Lu, Y. and Jiang, Y., 2022, October. Research on Mini-Batch Affinity Propagation Clus-tering Algorithm. In 2022 IEEE 9th International Conference on Data Science and Advanced Analytics (DSAA) (pp. 1-10). IEEE.
•	https://www.researchgate.net/publication/284938375_Impact_of_Distance_Measures_on_the_Performance_of_Clustering_Algorithms#:~:text=All%20these%20studies%20conclude%20that,for%20different%20distances.%20....
