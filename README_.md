# Capstone:  Identifying Color Themes in Vogue 
> **BOS DSI-8:** Callie Bouzane
---

## Problem Statement 

The aim of this project is to determine whether color is thematic in Vogue covers by testing whether color solely comprise the features in a Binary classification problem.  

This project will leverage (1) the Vogue Archive to gather images for 2,078 covers, and (2) OpenCV and KMeans to extract RGB values from the images to create a dataset to analyze color themes in Vogue covers.  Specifically, this will test whether or not color can be used to classify whether or not Anna Wintour was the editor in chief for a given publication.  The significance of these results can be used to further explore any color themes or trends.  

---

## The Process 

---

**Data Collection**

First, I needed to collect images of Vogue magazine covers.  Vogue has an excellent archive at https://archive.vogue.com/ of all issues from the present going back to the first issue in 1892.  Vogue's covers started to contain more color in the 1910's (although the first color photograph wasn't on the cover until 1932), so I web-scraped cover images from 1910 to present using BeautifulSoup.  

Once I had the images, 2,078 in total, I used OpenCV and KMeans clustering to quantify and collect data on color values in the images.  OpenCV was a critical in obtaining RGB values in an image.  

The data dictionary below outlines in detail the data in my final dataset, where each row was one of the 2,078 images I collected and the columns were the various features I created by extracting RGB values.


**Data Dictionary**

| Feature | Description |
| --- | --- |
| Date | Datetime format of the cover's publication date | 
| Month | Month of the cover's publication date |
| Year | Year of the cover's publication date | 
| Name | .jpg name of the cover's image |
| f# | frequency (in pixels) of an RBG value in a cover's image | 
| r# | value of R (red) in an RBG value | 
| g# | value of G (green) in an RBG value | 
| b# | value of B (blue) in an RBG value | 
| color# | the RBG array of r#, g#, b# | 
| xkcd# | the xkcd study color name that most closely matches the color#| 
| distance# | the distance between the xkcd# RBG array and the color# RBG array | 


**Model Summary**

I performed a Binary Classification Model on covers from 1950's to the present to determine whether an article was created while Anna Wintour (the current editor in chief) was editor in chief for a given cover in that time period.  

I decided to perform a Binary Classification Model on a smaller subset of my data to determine whether there is any significance in color that might be further explored on the full dataset.  I was please with having an R-squared of 72% on my testing data since it was above the baseline of ~60% and indicated that color has, in some way, evolved over time in the magazine's history.  

---

## Conclusions 

I was very pleased that my model ran better than the baseline.  My takeaway is that color could be used as a predictive variable for additional models, such as multi-classification for predicting the decade or season of a cover. 


**Next Steps**

1. Develop a time series 
2. Identify whether there are any trends in seasons and/or decades 
3. Create a multiclassification model for seasons and or/decades 
4. Create a KMeans Clustering model to identify any other potential trends 

---

## Sources 

https://blog.xkcd.com/2010/05/03/color-survey-results/
https://frankturnerv.com/portfolio/fashion-models-from-fashion-models/
https://towardsdatascience.com/color-identification-in-images-machine-learning-application-b26e770c4c71
https://scikit-image.org/docs/dev/auto_examples/transform/plot_histogram_matching.html#sphx-glr-auto-examples-transform-plot-histogram-matching-py
https://www.pyimagesearch.com/2014/08/04/opencv-python-color-detection/
https://archive.vogue.com/

