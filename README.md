# MachineLearningFinal
## Chineng "Cookie" Vang, Conner "Maurice" Hettinger, Ben Burgess

# Table of Contents
- [Pokemon Dataset](#pokemon-dataset)
    - [`Naive Attempt at Categorizing`](#naive-attempt)  
    - [`Attempt Based on Speed`](#speed-attempt)
    - [`Attempt Based on Ratio of Total Attack Stats to Total Defense Stats`](#ratio-attempt)
- [Letter Recognition Dataset](#letter-recognition-dataset)
- [Overall Results and Conclusion](#results-conclusion)

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

This was our second attempt at classifying the Pokemon dataset. It's corresponding code can be found in the ***pokemonSpeed.md*** file

* **Goal:** Based on the poor results from the first attempt, we chose to reduce the 18 types into 4 categories based on speed. How we went about this can be seen in a file we created called ***Average Pokemon Speed Based on Pokemon FireRed and Pokemon Emerald.csv***. We took the speed of every Pokemon in the games Pokemon FireRed and Pokemon Emerald and collected them in a spreadsheet, organizing it by the types of Pokemon. Then we found the average of the speeds and split up the types into the categories so that each category had a similar number of types. Our goal for this attempt was to classify Pokemon into one of the four categories: 
    * Super Slow (0): Fairy, Steel, Rock, Ground, Grass
    * Slow (1): Dark, Water, Ghost, Bug, Ice
    * Medium (2): Fire, Fighting, Normal, Poison
    * Fast (3): Dragon, Electric, Flying, Psychic

* **Hypothesis:** Our hypothesis is that this attempt would show higher overall accuracy than the first attempt because we reduced the number of categories so the neural network should be more confident in its response unilke last time. As people who have played Pokemon games, Pokemon that are certain types (Electric and Flying for example) usually stand out with their speed, so we thought we could get our testing accuracy to at least double from the 20% of the first attempt. 

* **Design Matrix:** 

![pokemon2DM](https://user-images.githubusercontent.com/60119741/166183297-415f620c-1156-43c3-a3d6-c85b72569149.jpg)


For preprocessing, we decided to only consider Pokemon with 2 types. In the last attempt, we omitted Type 2 from all Pokemon, so this time we wanted to try considering either all dual type Pokemon or all single type Pokemon to see if that made a difference. Considering all dual types also gave us a way to delete all entries with NA in the dataset. We again deleted the Generation column and used the same 7 features seen as we did for the first attempt. Each category/label was coded into a number (not ordered) ranging from 0 to 3. 

* **Process/Results of Attempt:** After filtering out all the single type Pokemon, our dataset was cut roughly in half to 414 data points/pokemon. We again did an 80/20 split for the training data and testing data respectively. We predicted correctly and saw our testing accuracy rise to about 44%, a significant increase from our  testing accuracy on the last attempt. We tried to increase the capacity of the network by adding more hidden layers and more nodes, but found that the testing accuracy generally became worse, probably overfitting.

### `Attempt Based on Ratio of Total Attack Stats to Total Defense Stats` <a name="ratio-attempt"></a>

This was our last attempt at using the Pokemon dataset. It's corresponding code can be found in the ***pokemonRatio.md*** file

* **Goal:** For this attempt, we divided the 18 types of Pokemon into 3 categories (low/mid/high) based on the ratio of their combined attack & special attack versus their combined defense and special defense. Essentially, is a pokemon type more likely to have a better offense or defense? As an example, a steel type pokemon on average has less attack power than it does defense, and a fire type pokemon on average has more attack power than it does defense Our categorization was based on the model from https://imgur.com/gallery/fGPnPFV: 
![pokemon3DM](https://user-images.githubusercontent.com/60119741/165883901-e2eecc9f-d12a-44d2-bebe-54266a4ce3e2.jpg) <br>
Our goal is to classify pokemon into either low, mid, or high:
    * Low (0): Ghost, Bug, Rock, Steel, Fairy
    * Mid (1): Water, Ground, Grass, Psychic, Ice, Poison, Normal
    * High (2): Electric, Flying, Dragon, Fighting, Fire, Dark

* **Hypothesis:** We did not think this attempt would yield a higher test accuracy than the second attempt, because although the graph above separates the types more distinctly than our previous two attempts (which helps the network answer more confidently), the values on the y-axis are within 0.5 of each other. Although the graph looks promising, the values still seem relatively close together. We thought that as a result, the network would again struggle to differentiate between the 3 categories, so we believed this would produce test accuracy more or less the same as the previous attempt. 

* **Design Matrix:** 

![pokemon3DM](https://user-images.githubusercontent.com/60119741/166188776-e9f83a30-1f8b-4fda-ba4b-4e5e3bb96a7c.jpg)


We did far more preprocessing than we did compared to the other two attempts. We took out Pokemon number, Name, Type 2, Total, HP, Speed, Generation, and Legendary status. That left 4 features: Attack, Defense, Special Attack, and Special Defense. We chose to do this to filter out noise and let the network only focus on the stats that truly matter. After little progress with considering dual type Pokemon in the second attempt, for this attempt, we chose to only consider Pokemon that have a single type. It isn’t unusual when a dual type Pokemon (say Heracross, a Pokemon that is a bug and fighting type) has a type that contradicts the other. Using Heracross as an example, bug types usually have a low attack stat, but because Heracross is also a fighting type, its attack is very high. This makes Heracross hard to categorize because the high attack stat would suggest to the model that Heracross is not a bug type. The three categories were labeled 0 through 2.

* **Process/Results of Attempt:** After filtering out the dual types, the dataset was left with 386 Pokemon. We again did an 80/20 split for the training data and testing data respectively. We were pleasantly wrong on this attempt, and saw a vast improvement on the testing accuracy, which ranged from 60-70%. This was by far our best attempt, but the network was still overfitting. To address this, we implemented L2 regularization as a way to reduce the weights and generalize the network. The addition of regularization was successful, as we found our training and testing data exhibiting very similar accuracies. We also tried the L2 regularization along with increasing the capacity by adding extra hidden layers and increasing the number of nodes per hidden layer to 128. This didn't seem to make much of a difference and sometimes wouuld worsen the testing accuracy. 

## Letter Recognition Dataset 

The goal is to use a classification network in order to recognize hand written letters. We made each letter its own category and gave the neural network numerical information about each letter (described below). We based our neural network on the iris example, with two layers of 64 nodes with relu as an activation function and a final layer with softmax as an activation function. Softmax was good to use becaue we are trying to categorize the data. Relu was nice because it is simple and efficient. With this setup, by the third epoch the neural network had over 90% accuracy. By the end it averages 99.4% accuracy with no drop off after evaluating the testing data. We then attempted to increase the amount of hidden layers and nodes to see how it would affect accuarcy/loss. In both scenarios they were pretty close to being identical. It would vary randomly between 97%-99% every time we reran it. 

We did not want to use a recurrent neural network because the data is nonsequential. Also, we did not want to use convolutional neural networks because there was no data compression and feed forwards was easier to use. 

![Screenshot from 2022-04-29 13-35-57](https://user-images.githubusercontent.com/60119741/166005668-088a044e-bda2-4a2d-916e-d827c69849e7.png)

^The top graph is loss and the bottom graph is accuracy^

We started by randomly using 19500 of the examples as training and then 500 as testing data. This yielded the result of approximately 98% accuracy. Then we tried using 16000 examples of training and 4000 examples of testing and it yielded the same resault. 

This data set worked really well because of the large data set. We found that this one was easy to work with and easy to get good resaults because there is a lot of attribute information about each letter. The information also directly corresponds to the category and each category is well represented. The pokemon dataset was hard to work with because there was only 800 total samples and each category was vastly different in size. So it was fairly common for us to run into the issue that the neural network would always choose the majority category because it could achieve high accuracy in the training model.

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

## Overall Results and Conclusion <a name="results-conclusion"></a>
We found that overall the pokemon dataset was difficult to work with. The type of the pokemon does not correlate to the pokemon's stats in any meaningful way. We found this out when our best earliest attempts had an accuracy of 25%. Even after tinkering with the dataset to create better circumstances, we found that there was no way to recategorize the dataset to create correlation. We tried to narrow the types down to three categories defined by speed, which resulted in us having two minority categories that went underrepresented. We then expanded to four speed categories which also had the same underrepresentation for the super fast category and slowest category. Finally we split the cateogries in a similar way but corresponding to attack-defence ratio. With this method we had three categories: low, mid, and high. We believe it worked better this way because there was more of a definitive difference between categories.
