# MachineLearningFinal
## Chineng "Cookie" Vang, Conner "Maurice" Hettinger, Ben Burgess

# Table of Contents
- [Pokemon Dataset](#pokemon-dataset)
    - [`Naive Attempt at Categorizing`](#naive-attempt)  
    - [`Attempt Based on Speed`](#speed-attempt)
    - [`Attempt Based on Ratio of Total Attack Stats to Total Defense Stats`](#ratio-attempt)
    - [`Overall Results and Conclusion`](#results-conclusion)
- [Letter Recognition Dataset](#letter-recognition-dataset)

## Pokemon Dataset

The data set we initially looked at was the stats of Pokemon from this site: https://gist.github.com/armgilles/194bcff35001e7eb53a2a8b441e8b2c6. The stats of a Pokemon include: Pokedex Number, Name, Type 1, Type 2, Total, HP (hit points), Attack, Defense, Special Attack, Special Defense, Speed, Generation, and Legendary status. (insert what is the structure for our neural network here since it's the same for each attempt)

### `Naive Attempt at Categorizing` <a name="naive-attempt"></a>

This was our first attempt at classifying the dataset and the corresponding code is in the ***pokemonNaive.md*** file.

![pokemonTypes](https://user-images.githubusercontent.com/60119741/165833698-ddbb4d76-e68b-49cd-b343-d9e2da98d4f1.png)

* **Goal:** There are 18 types of Pokemon seen above. Our goal was to classify a Pokemon's Type 1 based on its battle stats (Total, HP, Attack, Defense, Special Attack, Special Defense, and Speed).
* **Hypothesis:** Our initial hypothesis was that the neural network would do a really bad job at classifying the Pokemon because there 18 types/categories. Since the output layer adds up to 1 which is spread throughout the 18 possibilities, the neural network will not answer with a lot of confidence.
* **Design Matrix:** 

![pokemon1DM](https://user-images.githubusercontent.com/60119741/165838581-fa6c1b6a-12ee-4ab9-b89e-046a522e968e.jpg)

Some preprocessing we did to the data in this attempt was delete the Type 2 column for all the Pokemon because not all Pokemon have a second type, so that value showed as NA. We also deleted the Generation column since a Pokemon's generation contributes nothing to a Pokemon's type.  We had 7 features seen in the image above and our labels were the Pokemon's type. Each type was coded into a number (not ordered) ranging from 0 to 17. 

* **Process/Results of Attempt:**  We used all 800 data points/pokemon and did an 80/20 split for the training data and testing data respectively. Since Pokemon are designed uniquely, we didn't want the training data to specialize on the Pokemon we gave it, so we opted to hand it less data with the 80/20 split versus a 90/10 split. As predicted, we had poor training and test accuracy with test accuracy usually around 20%. We tried to increase the capacity of the network by adding more hidden layers and more nodes, but the results didn't budge at all. We then prioritized getting our accuracy up versus overfitting, so we doubled the number of epochs and found the testing accuracy was raised by about 5%.  With both the training and test accuracy really low, we did not utilize regularization on this attempt. 

### `Attempt Based on Speed` <a name="speed-attempt"></a>

This was our second attempt at classifying the Pokemon dataset.

* **Goal:** Based on the poor results from the first attempt, we chose to reduce the 18 types into 4 categories based on speed. How we went about this can be seen in a file we created called ***Average Pokemon Speed Based on Pokemon FireRed and Pokemon Emerald.csv***. We took the speed of every Pokemon in the games Pokemon FireRed and Pokemon Emerald and collected them in a spreadsheet, organizing it by the types of Pokemon. Then we found the average of the speeds and split up the types into the categories so that each category had a similar number of types. Our goal for this attempt was to classify Pokemon into one of the four categories: 
    * Super Slow (0): Fairy, Steel, Rock, Ground, Grass
    * Slow (1): Dark, Water, Ghost, Bug, Ice
    * Medium (2): Fire, Fighting, Normal, Poison
    * Fast (3): Dragon, Electric, Flying, Psychic

* **Hypothesis:** Our hypothesis is that this attempt would show higher overall accuracy than the first attempt because we reduced the number of categories so the neural network should be more confident in its response unilke last time. As people who have played Pokemon games, Pokemon that are certain types (Electric and Flying for example) usually stand out with their speed, so we thought we could get our testing accuracy to at least double from the 20% of the first attempt. 

* **Design Matrix:** 

![pokemon2DM](https://user-images.githubusercontent.com/60119741/165854823-d9f580ca-3241-4c5d-91af-f793cdf5cb46.jpg)

For preprocessing, we decided to only consider Pokemon with 2 types. In the last attempt, we omitted Type 2 from all Pokemon, so this time we wanted to try considering either all dual type Pokemon or all single type Pokemon to see if that made a difference. Considering all dual types also gave us a way to delete all entries with NA in the dataset. We again deleted the Generation column and used the same 7 features seen as we did for the first attempt. Each category/label was coded into a number (not ordered) ranging from 0 to 3. 

* **Process/Results of Attempt:** After filtering out all the single type Pokemon, our dataset was cut roughly in half to 414 data points/pokemon. We again did an 80/20 split for the training data and testing data respectively. We predicted correctly and saw our testing accuracy rise to about 44% we had poor training and test accuracy with test accuracy usually around 20%. We tried to increase the capacity of the network by adding more hidden layers and more nodes, but found that the testing accuracy generally became worse, probably overfitting.

### `Attempt Based on Ratio of Total Attack Stats to Total Defense Stats` <a name="ratio-attempt"></a>

dfd

### `Overall Results and Conclusion` <a name="results-conclusion"></a>

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

