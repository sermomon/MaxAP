# Maximum Average Probability (MaxAP)

MaxAP is a method for the classification of agricultural plots from satellite or aerial images employed in (Morell-Monzó et al, 2023). The method allows to classify a spatial database of polygons (LPIS - Land Parcel Identification System) from a semantically segmented image.

The proposed method is described below:
1.	A supervised classification model is trained using pixels as training samples (i.e. Random Forest). Only pixels completely covered by the parcels are used for training.
2.	Then the fitted model is used to predict the probability of each pixel being in each class. Therefore, for each pixel of the image, a probability vector with length C is predicted, being C the number of classes. In this work the number of classes is 3.
3.	Finally, parcel-based classification is performed. For each parcel, the average probability of each class is calculated using the full pixels inside the parcel boundaries (Figure 5). Full pixels are those that have a coverage threshold of 100%, however, the method iteratively reduces this threshold to 75% and 50% in case there are no full pixels inside the parcel boundaries. Finally, each parcel is assigned the class with the maximum probability.

![Imagen1](https://user-images.githubusercontent.com/59225676/204855750-5c82dfed-9ec3-4143-bf40-ff3e90fab07f.png)

where *i* is the number of pure pixels in the parcel *N*, and *j* is the number of classes.
