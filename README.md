# Public Transportation Optimization through Clustering in France

## Introduction
In this project, we embarked on an analytical journey to enhance the efficiency and reliability of a public transportation system. The primary objective was to identify patterns and inefficiencies within the system, focusing on aspects such as train delays, travel times, and the punctuality of arrivals and departures. By leveraging the k-means clustering technique, our goal was to categorize different segments of the transportation service, aiming to pinpoint specific areas that could benefit from targeted improvements.

Through a detailed data-driven approach, employing methods like the elbow method for optimal cluster determination and meticulous data normalization, we sought to uncover underlying trends and clusters within the transportation data. This project not only aimed to provide actionable insights for transportation optimization but also served as a testament to the transformative power of data analysis in operational management.

## About the Data
The dataset utilized in this project was sourced from Kaggle, specifically the ["Public Transport Traffic Data in France"](https://www.kaggle.com/datasets/gatandubuc/public-transport-traffic-data-in-france) dataset. This dataset provides a comprehensive view of the public transportation system in France, encompassing a wide array of metrics that reflect the operational dynamics of train services.

#### Dataset Overview
The dataset is rich in both breadth and depth, offering a detailed snapshot of various aspects of public transportation. Key features include:
- **Number of Late Trains (> 15min)**: This measures the count of trains experiencing significant delays.
- **Average Delay of Late Departing Trains (min)**: A metric capturing the average delay encountered by trains that departed later than scheduled.
- **Number of Trains Late on Arrival**: The total number of trains that arrived at their destination behind schedule.
- **Average Travel Time (min)**: Reflects the mean travel duration for the trains within the dataset.

These features were pivotal in our analysis, enabling us to dissect the performance of the train services across different dimensions.

All of the columns present in our dataset are shown below:

![In-Depth Column Information](visualizations/ColumnInfo.png)

#### Dataset Size and Statistics
The dataset comprises a substantial number of records, offering a robust foundation for our analysis. The size and diversity of the data ensured that our findings and insights were grounded in a comprehensive understanding of the transportation system's dynamics.

#### Data Pre-processing and Exploration
The initial steps in our project included cleaning and preprocessing the data. We handled missing values, standardized the features for uniformity, and conducted exploratory data analysis to gain preliminary insights. This phase was crucial in shaping our approach to clustering and further analysis.

Noticing that the “Comment (optional) delays at departure” column was full of null values, we removed it entirely using the following method:
`df_1.drop(columns=['Comment (optional) delays at departure'])`

Our model was able to perform perfectly fine without any further adjustments.

#### Visualizations
Throughout the project, various visualizations were created to aid in understanding the data. These included the Elbow Method plot to determine the optimal number of clusters for k-means and scatter plots to visualize the resulting clusters. These visualizations not only provided clarity on the data structure but also helped in communicating our findings effectively.

In summary, the "Public Transport Traffic Data in France" dataset from Kaggle served as the backbone of our analysis, offering a detailed and comprehensive view of the public transportation system in France. The dataset's rich features and substantial size played a crucial role in enabling a deep and insightful exploration into the operational efficiencies of the train services.


![Distribution Of Average Travel Times](visualizations/DistributionOfAverageTravelTimes.png)

The histogram above illustrates the distribution of average travel times for the public transport system under study. It appears that the travel times are concentrated in several peaks, suggesting that there may be common route lengths or that certain travel times are more frequent than others. There's a significant peak around the 100-200 minute mark, indicating a large number of routes fall within this travel time range. The long tail to the right suggests there are fewer routes with very long travel times, possibly representing longer-distance services. This visualization aids in understanding the distribution of travel times across the public transportation network, which is an essential aspect of optimizing the system's efficiency.


![Boxplot of Number of Cancelled Trains](visualizations/BoxplotOfNumberOfCancelledTrains.png)

The boxplot provides a visual summary of the distribution of canceled trains. It indicates the median, spread, and outliers in the data, helping to identify stations with unusually high numbers of cancellations. This can guide resource allocation for improving reliability or addressing specific issues leading to cancellations.


![Boxplot of Number of Late Trains at Departure](visualizations/BoxplotOfNumberOfLateTrainsAtDeparture.png)

Similar to the boxplot for cancellations, this one focuses on the number of late trains at departure. It offers insights into the consistency of train departures across the network. Stations that show a high range or outliers might need specific attention to improve their on-time departure rates.


![Average Delay by Departure Station](visualizations/AverageDelayByDepartureStation.png)

This horizontal bar chart presents the average delay times by departure station. It highlights the variability in punctuality across stations, with some stations consistently experiencing delays while others often depart ahead of schedule. This visualization can be instrumental in pinpointing problem areas within the network where interventions could improve overall efficiency.


![Correlation Matrix of Numeric Features](visualizations/CorrelationMatrixOfNumericFeatures.png)

The correlation matrix uses color intensity to represent the strength and direction of the relationship between different numerical features of the data set. This heat map is a powerful tool for quickly understanding how different factors relate to each other, which can be vital for building predictive models or understanding the underlying causes of delays and cancellations.


## Methods
Our project's analytical journey began with preprocessing, where we addressed missing values and normalized our dataset. Given the centrality of numeric columns in clustering, we selected features that captured the essence of public transportation performance: the number of late trains, average delays, and average travel times. We filled missing values with column means to maintain the dataset's integrity.

![Elbow Method](visualizations/ElbowMethodAnnotated.png)

The k-means clustering algorithm was at the heart of our model, and we used the Elbow method to determine the optimal number of clusters. By plotting the Within-Cluster-Sum of Squares (WCSS) against the number of clusters, we looked for the 'elbow' point where the reduction in WCSS starts to diminish, indicating the most appropriate cluster count for our data. After several iterations, we finalized four as the optimal number, providing a balance between model complexity and meaningful segmentation.


We experimented with different combinations of features and scaling methods to refine our clusters, seeking patterns that could inform actionable insights for improving public transportation systems. Each iteration offered a deeper understanding, whether through revealing overlaps between clusters or identifying outliers.

Visualizations played a crucial role, in turning complex multidimensional data into comprehendible plots. The final clustering visualization offered a clear distinction between groups, aiding in the interpretation and subsequent decision-making process.

Throughout these stages, we iterated on our approach, reflecting on what worked and what didn't. We continually sought to improve our model, gaining new insights into public transportation dynamics with each step. The iterative process not only fine-tuned our model but also deepened our understanding of the data and its implications for public transportation management.

## Evaluation
The evaluation of our k-means clustering model's performance was primarily qualitative, as clustering models do not have a definitive accuracy measure like supervised learning models. The Elbow method served as our initial evaluation tool, helping us to discern the point of diminishing returns in adding more clusters. With the Elbow plot indicating four as the optimal number of clusters, we proceeded to visualize the data.

![Clusters of Trains](visualizations/ClustersOfTrains.png)

The final cluster visualization is a key component of our evaluation. It displays a clear separation among the four clusters, each representing distinct groupings of the public transportation system's performance metrics. The clusters were named based on their defining characteristics, which were gleaned from their centroids and distribution across the feature space. These names – such as "Swift Starters" for those with low delays and travel times, and "Extended Delay Commuters" for those with the highest delays – provide intuitive insights into each group's performance. If visualized in a 3D space, the "Timeliness Travelers" cluster would likely exhibit clear spatial separation above the blue and red clusters, revealing the distinct group characteristics that are obscured in two dimensions.

While traditional metrics like accuracy, f1 score, and precision are not applicable, we evaluated cluster cohesion and separation to ensure meaningful groupings.

Our visualization and analysis of the clusters allowed us to answer key questions posed in the introduction. We identified patterns and anomalies in public transportation performance, such as stations consistently experiencing delays and trains that are frequently late or have longer travel times. The insights drawn from our clusters align with our goal of optimizing the public transportation system by identifying potential areas for improvement.

## Storytelling and Conclusion
By applying the elbow method and k-means clustering to key performance indicators such as delays and travel times, we've segmented trains into distinct operational profiles. These clusters with significant variability, each tell a story of operational efficiency and areas for improvement. Our initial goal was to identify patterns that could enhance scheduling and reliability. The insights gained have laid the groundwork for targeted improvements. This project has underscored the power of data-driven decision-making in public transport management. Future steps would include refining the model with real-time data feeds and exploring predictive analytics to pre-emptively manage delays.

## Impact
The implementation of k-Means clustering to optimize public transportation offers significant social benefits, primarily by enhancing the reliability and efficiency of train schedules, thus potentially improving the daily commute for thousands of individuals. By reducing delays and identifying bottleneck stations, the project can contribute to a decrease in traveler stress and an increase in overall satisfaction with public transport services. On an environmental level, improved punctuality may encourage a shift from car travel to public transit, aiding in the reduction of urban traffic congestion and carbon emissions.

Ethically, however, the project must navigate the fine line between operational efficiency and the quality of work-life balance for transportation staff. Changes to schedules and increased efficiency demands could inadvertently lead to worker strain. Moreover, there's the risk of data privacy concerns when integrating real-time data feeds, especially if the personal data of commuters are involved without explicit consent. Lastly, while enhancing one aspect of the transportation system, we must ensure equitable improvements across all routes to avoid disproportionately favoring more profitable or busier lines, thereby maintaining fairness in service provision. The project's execution must remain mindful of these potential impacts, striving for a balance that maximizes benefit while minimizing harm.

## Dataset
- https://www.kaggle.com/datasets/gatandubuc/public-transport-traffic-data-in-france

