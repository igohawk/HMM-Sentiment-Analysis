# Machine Learning Project Report
## Part 2:
First, we split data into tuples for each single tweet.Then we write a function that 
estimates the emission parameters from the training set using MLE (maximum likelihood estimation):

e(x|y) = Count(y -> x)/Count(y)

with key <word, tag>. To smooth the data, during the testing phase, if the word does not appear 
in the training set, we replace that word with the special word token #UNK#. 

We set k to 1 when modifying the computation of emission probabilities. Then we implement a simple sequence 
labeling system that produces the tag for each word x in the sequence.

The evaluation results are as follows:
CN
Entities:
In gold-standard outputs: 1081
In prediction outputs: 3963

Entities Correct: 485
Entities F score: 0.1923 (Precision: 0.1224, Recall: 0.4487)

Sentiment Correct: 347
Sentiment F score: 0.1376 (Precision: 0.0876, Recall: 0.3210)

EN
Entities:
In gold-standard outputs: 802
In prediction outputs: 770

Entities Correct: 489
Entities F score: 0.6221 (Precision: 0.6351, Recall: 0.6097)

Sentiment Correct: 448
Sentiment F score: 0.5700 (Precision: 0.5818, Recall: 0.5586)

SG
Entities:
In gold-standard outputs: 4092
In prediction outputs: 9283

Entities Correct: 1999
Entities F score: 0.2989 (Precision: 0.2153, Recall: 0.4885)

Sentiment Correct: 1179
Sentiment F score: 0.1763 (Precision: 0.1270, Recall: 0.2881)

FR
Entities:
In gold-standard outputs: 238
In prediction outputs: 826

Entities Correct: 175
Entities F score: 0.3289 (Precision: 0.2119, Recall: 0.7353)

Sentiment Correct: 78
Sentiment F score: 0.1466 (Precision: 0.0944, Recall: 0.3277)

## Part 3:

## Part 4: 
### Implementation
Similar to the 1-order Viterbi Algorithm, the calculation of emission parameters is the same as in part 2 and part 3. The transition parameters used in the decoding process are taken to be the MLE of the transition probabilities of a trigram of tag sequence, expressed as follows:

![alt text](https://render.githubusercontent.com/render/math?math=p%28y_%7Bi%7D%5C%3B%7C%5C%3By_%7Bi-2%7D%2Cy_%7Bi-1%7D%29%3D%5Cfrac%7Bp%28y_%7Bi-2%7D%2Cy_%7Bi-1%7D%2Cy_%7Bi%7D%29%7D%7Bp%28y_%7Bi-2%7D%2Cy_%7Bi-1%7D%29%7D%3D%5Cfrac%7BCount%28y_%7Bi-2%7D%2Cy_%7Bi-1%7D%2Cy_%7Bi%7D%29%7D%7BCount%28y_%7Bi-2%7D%2Cy_%7Bi-1%7D%29%7D&mode=display)

It could also be written as ![alt text](https://render.githubusercontent.com/render/math?math=p%28v%5C%3B%7C%5C%3Bw%2Cu%29%3D%5Cfrac%7BCount%28w%2Cu%2Cv%29%7D%7BCount%28w%2Cu%29%7D&mode=display)
 , where the tag sequence is w -> u -> v.


### 2-order Viterbi Algorithm

![alt](https://github.com/igohawk/machine-learning-project/blob/master/p4_image_1.png?raw=true)


### Most likely tag sequences
It is easier to obtain the most likely tag sequence with given next tag:
![alt](https://github.com/igohawk/machine-learning-project/blob/master/p4_image_2.png?raw=true)


### Time complexity
To calculate the score for each possible tag at a time, we need to do the calculation for all of the combinations of (w,u,v), where w is the previous tag, u is the current tag and v is the next tag. For time=1 to time=n, we will have three loops at each time step. Therefore, the total complexity is given by O(nT^3)

## Part 5
