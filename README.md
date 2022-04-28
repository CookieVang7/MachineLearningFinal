# MachineLearningFinal
## Chineng "Cookie" Vang, Conner "Maurice" Hettinger, Ben Burgess

# Table of Contents
- [Pokemon Dataset](#pokemonDataset)
    - [`Naive Attempt at Categorizing`](#naitveAttempt)  
    - [`Attempt Based on Speed`](#speedAttempt)
    - [`Attempt Based on Ratio of Total Attack Stats to Total Defense Stats`](#ratioAttempt)
- [Letter Recognition Dataset](#letterRecognition)

## Pokemon Dataset

words here

### Naive Attempt at Categorizing

dfd

### Attempt Based on Speed

dfd

### Attempt Based on Ratio of Total Attack Stats to Total Defense Stats

dfd

## Letter Recognition Dataset

We found a dataset that took 20,000 pictures of drawn letters and converted them into information (as shown below). Then we based our neural network on the example, with two layers of 64 nodes with relu as an activation function and a final layer with softmax as an activation function. With this setup, by the third epoch the neural network had over 90% accuracy. By the end it averages 99.4% accuracy with no drop off after evaluating the testing data. 

This seems to be better overall for the neural network because there are tons of examples of letters being processed from each category (a-z). Whereas the pokemon dataset only had 600 examples with extremely imbalanced categories. Also we found that pokemon type is fairly independent from its stats, so in this case the information being processed is more related to the category we are trying to guess. 

**Attribute Information:**
1. lettr capital letter (26 values from A to Z)
2. x-box horizontal position of box (integer)
3. y-box vertical position of box (integer)
4. width width of box (integer)
5. high height of box (integer)
6. onpix total # on pixels (integer)
7. x-bar mean x of on pixels in box (integer)
8. y-bar mean y of on pixels in box (integer)
9. x2bar mean x variance (integer)
10. y2bar mean y variance (integer)
11. xybar mean x y correlation (integer)
12. x2ybr mean of x * x * y (integer)
13. xy2br mean of x * y * y (integer)
14. x-ege mean edge count left to right (integer)
15. xegvy correlation of x-ege with y (integer)
16. y-ege mean edge count bottom to top (integer)
17. yegvx correlation of y-ege with x (integer)
