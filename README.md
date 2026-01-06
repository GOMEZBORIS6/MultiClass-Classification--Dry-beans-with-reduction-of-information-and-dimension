# MultiClass-Classification--Dry-beans-with-reduction-of-information-and-dimension
<center>

**Can you predict the type of a [dry bean](https://archive.ics.uci.edu/dataset/602/dry+bean+dataset) from its shape features?**

</center>

***

<img style="width:100%; height: 400px" alt="Image" src="https://github.com/user-attachments/assets/a57271ce-9d02-4b31-bda5-021c66733eee" />

## **Overview:**

<div style='text-align: justify;'>

In this project, our goal is to predict the type of dry beans based on characteristics such as shape and structure, taking into account the market situation. The classification model was developed using a high-resolution camera to capture images of **13,611 grains** from these seven registered dry bean varieties. Bean images obtained through a computer vision system underwent segmentation and feature extraction stages, resulting in a total of **16 features**; **12 dimensions** and **4 shape** forms extracted from the grains. Various machine learning algorithms and deep learning algorithms were employed in this project to classify the most well-known 7 types of beans in Turkey: `Barbunya`, `Bombay`, `Cali`, `Dermason`, `Horoz`, `Seker`, and `Sira`. The classification was based solely on dimension and shape features of bean varieties, without incorporating external discriminatory features. Additionally, dimensionality reduction and non-collinearity methods were applied due to the high dimensionality of our dataset and the presence of correlated variables. The method used include is Principal Component Analysis called PCA because many variables is correlated and in our case all explanatory variables is continuous. The data are also unbalanced, especially for dry beans, where the class was 3.85%. For this reason, we implemented the **over-sampling** technique with ***SMOTE (Synthetic Minority Oversampling Technique)***. Over-sampling involves increasing the number of observations from the minority class to mitigate the imbalance. With the ***Deep learning model, 12 Machine Learning classification algorithms*** were implemented and the best model retained with the best performance on the Test data was the ***Random Forest with 91.99%***. We therefore looked at how each of our variables contributes to prediction in this model with ***Shapley Values***. Three variables have the least effect in the classification of the Random Forest model: Extent, solidity, shapeFactor2. After reimplementing the Random Forest without these variables, we obtained an accuracy of ***95.09%***.


</div>


### *Dataset Description*
<table>
    <tr>
        <th><center> Name </center></th>
        <th><center> Type </center></th>
        <th><center> Values </center></th>
        <th><center> Description </center></th>
    </tr>
    <tr>
        <td><center> Area (A) </center></td>
        <td><center> Integer </center></td>
        <td><center> From 20420 to 254616 </center></td>
        <td><center> The area of a bean zone and the number of pixels within its boundaries. </center></td>
    </tr>
    <tr>
        <td><center> Perimeter (P) </center></td>
        <td><center> Continuous </center></td>
        <td><center> From 524.74 to 1985.37 </center></td>
        <td><center> Bean circumference is defined as the length of its border. </center></td>
    </tr>
    <tr>
        <td><center> MajorAxisLength (L) </center></td>
        <td><center> Continuous </center></td>
        <td><center> From 183.60 to 738.86 </center></td>
        <td><center> The distance between the ends of the longest line that can be drawn from a bean. </center></td>
    </tr>
    <tr>
        <td><center> MinorAxisLength (l) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 122.51 to 460.19 </center></td>
        <td><center> The longest line that can be drawn from the bean while standing perpendicular to the main axis. </center></td>
    </tr>
    <tr>
        <td><center> AspectRatio (K) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 1.02 to 2.43 </center></td>
        <td><center> Defines the relationship between MajorAxisLength(L) and MinorAxisLength(l). </center></td>
    </tr>
    <tr>
        <td><center> Eccentricity (Ec) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 0.21 to 0.91 </center></td>
        <td><center> Eccentricity of the ellipse having the same moments as the region. </center></td>
    </tr>
    <tr>
        <td><center> ConvexArea (C) </center></td>
        <td><center> Integer </center></td>
        <td><center> From 20684 to 263261 </center></td>
        <td><center> Number of pixels in the smallest convex polygon that can contain the area of a bean seed. </center></td>
    </tr>
    <tr>
        <td><center> EquivDiameter (Ed) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 161.24 to 569.37 </center></td>
        <td><center> Equivalent diameter: The diameter of a circle having the same area as a bean seed area. </center></td>
    </tr>
    <tr>
        <td><center> Extent (Ex) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 0.55 to 0.86 </center></td>
        <td><center> The ratio of the pixels in the bounding box to the bean area. </center></td>
    </tr>
    <tr>
        <td><center> Solidity (S) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 0.91 to 0.99 </center></td>
        <td><center> Also known as convexity. The ratio of the pixels in the convex shell to those found in beans. </center></td>
    </tr>
    <tr>
        <td><center> Roundness (R) </center></td>
        <td><center> Continuous </center></td>
        <td><center> From 0.48 to 0.99 </center></td>
        <td><center> Calculated with the following formula: (4* pi * A)/(P^2) </center></td>
    </tr>
    <tr>
        <td><center> Compactness (CO) </center></td>
        <td><center> Continuous </center></td>
        <td><center> From 0.64 to 0.98 </center></td>
        <td><center> Measures the roundness of an object: Ed/L  </center></td>
    </tr>
    <tr>
        <td><center> ShapeFactor1 (SF1) </center></td>
        <td><center> Continuous </center></td>
        <td><center> From 0.002 to 0.010 </center></td>
        <td><center> L/d </center></td>
    </tr>
    <tr>
        <td><center> ShapeFactor2 (SF2) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 0.000 to 0.003 </center></td>
        <td><center> l/d </center></td>
    </tr>
    <tr>
        <td><center> ShapeFactor3 (SF3) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 0.41 to 0.97 </center></td>
        <td><center> 4A/(L^2 * pi) </center></td>
    </tr>
    <tr>
        <td><center> ShapeFactor4 (SF4) </center></td>
        <td><center> Continuous  </center></td>
        <td><center> From 0.94 to 0.99 </center></td>
        <td><center> 4A/(L* l * pi) </center></td>
    </tr>
    <tr>
        <td><center> Class </center></td>
        <td><center> Nominal  </center></td>
        <td><center> It can be any of BARBUNYA, SIRA, HOROZ, DERMASON, CALI, BOMBAY, and SEKER. </center></td>
        <td><center> The class of the bean. </center></td>
    </tr>

</table>


### Algorithms Implemented
1. Elastic Net Logistic Regression
2. Random Forest
3. GradientBoosting
4. Neural Network
5. Support Vector Machine
6. K-Nearest Neighbors
7. XGBoost
8. Decision Tree
9. Naives Bayes
10. Stochastic Gradient Descent
11. AdaBoost
12. Ridge Classifier
13. Deep Learning with 4-layers (128, 64, 32 and 7 neurons) and two activations functions: ReLU and Linear.
