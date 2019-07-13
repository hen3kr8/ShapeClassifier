# Logistic Regression Shape Classifier


I created a simple triangle/circle classifier from scratch using logistic regression to learn how neural newtworks work.

How this works, as simply as possible:

##Input:

Our input data, *x* (which is a collection of 200px by 200px images of either triangles or circles) is flattened. This is our training data.

Our training data also has labels, 0 if it is a circle and 1 if it is a triangle.
We will call this collection of labels *y*.

##Forward Propogation:

*x* is multiplied by our weights, *w*, and a bias *b* is added to give us z.

Our weights and bias is initialised to 0.01 and 0 respectfully.

*z = xw + b*

###Activation function:

*z* is then pushed through the activation function (basically takes the value and classifies it as either 0 or 1) to produce the prediction of y, *y_pred*, given *z*. The activation function used here is a sigmoid function.

```y_pred = sigmoid(z)*```

###Loss function:

We now compare *y* (the actual labels of our images) to *y_pred*.

We calculate the mean squared error of all *y_pred* and *y*. The result is the **cost**, which shows how well our model is currently performing with the given weights and bias.
*Note that *y* and *y_pred* are vectors.

##Back Propogation:

We update our weights and bias, by calculating:

*a* = the dot product of *x* and *(y_pred - y).T* times scaling factor (which we specify)
*b* =  sum of *(y_pred - y)*

*new_weight* = *old_weight* - learning_rate times (*a*)
new_bias = old_bias* - learning_rate times (*b*)


And now we do forward propogation again, but now with our new weights and bias. The process can be repeated untill an satisfying cost is reached.

After the model has been built, we test it using test data (data which the model has never seen before) and evaluate its preformance.

##Results:

The model achieves a cost of 0 after 20 iterations. This means not one image was classified incorrectly after only 20 iterations. So the model has a accuracy of 100%.

This is however, not a good thing. This is what is called over fitting. Taking a closer look at the data shows that there is too little variation: 
Almost all cirlcle images look identical; they all occur in the exact center of the image, are about the same size, and are filled in every case. The triangles differ slightly more but still contain way too little variation.

The reason why overfitting is bad, is that given a circle that does not conform to the training data, (i.e. not filled, smaller or not centered) it will could be misclassified.

The purpose of this code was to learn how a neural network, logistic logression in particlar, work and not make an amazing shape classifier. I learned much about this topic and I would like to create a model that is able to find waldo.

The data is from
https://www.kaggle.com/smeschke/four-shapes

(I followed a tutorial on how to build a neural network, which I for the life of me cannot seem to locate, I apologize)
