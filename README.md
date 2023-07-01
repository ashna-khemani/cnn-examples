# CNN Examples
Examples of Convolutional Neural Networks in action! 

## Running these notebooks
The easiest way to run these notebooks is through <a href="https://colab.research.google.com">Google Colab</a>, but you can also run them locally on your computer.
If you choose to run locally, I recommend using a virtual environment, especially if you don't have libraries like tensorflow installed globally.   
Here's how to do that (for Mac users):
1. Make sure you have virtualenv installed   
    1. Check this by running `pip show virtualenv`
    2. Not there? Run `pip install virtualenv`
2. Start a virtual environment (I like calling mine .env)
    1. Navigate to your project folder in your Terminal
    2. Run `virtualenv .env`
    3. Run `source .env/bin/activate`

Now we're in the virtual env! You will probably need to install `tensorflow` and `matplotlib`. Run the following:
* `pip install tensorflow`
* `pip install matplotlib`

I personally ran into some permission errors when installing tensorflow. If you also have that issue, try running `pip install --no-cache-dir tensorflow`. This essentially ignores the cache that is restricted. Not really much of an effect, except the installation taking slightly longer. You can also try `sudo pip install tensorflow` but it's not the safest habit in the world.

*Note: depending on your Python installation, you might be better off using `pip3` instead of `pip` for these commands*   


## Basic Theory
A **neural network** is a series of connected nodes arranged in layers. We have an **input layer**, a number of **hidden layers**, and an **output layer**. 
<br>

<a href="https://towardsdatascience.com/applied-deep-learning-part-1-artificial-neural-networks-d7834f67a4f6"><img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Gh5PS4R_A5drl5ebd_gNrg@2x.png" height=300></a>
<br>

The number of nodes in the output layer corresponds to the number of classes we have. For example, in the `flower_classification` example, we have 5 different classes of flowers (roses, daisies, sunflowers, tulips, dandelions), so our output layer will have 5 nodes. Each output node represents the probability that a datapoint (an image) belongs to that class.
<br>

Each **synapse**, or connection, between nodes is assigned a mathematical **weight**. These can very broadly be thought of as the importance between certain properties (very rough example: we might see a low weight between the node of bright yellow of a sunflower and the node representing daisies; they're not that related). Pretty hand-wavy definition for people who aren't keen on math, but if you want more specifics, the image above is linked to a pretty good article.
<br>

The goal of a neural net is to adjust these weights until it can make reliable an accurate classifications. It does this by passing the whole dataset through itself multiple times, calculating the **loss** (how poorly it performed) and adjusting the weights of each synapse accordingly. Often, we do this in **batches**; instead of passing the *entire* dataset before adjusting the weight, we pass a small batch of a few images, then adjust the weights, pass the next batch, adjust the weights... and so on until we cover the whole dataset.
<br>

However, remember we also go over the *entire dataset* multiple times! Each run over the whole dataset is called an **epoch**.
<br>

**Okay, so whats a *convolutional* NN?** That boils down to "messing" with the data a lot before passing it through the NN. Stretching images, flipping them, rotating them, zooming... distoring them in multiple ways so the NN can theoretically recognize the subject from any view/perspective. This process is called **data augmentation**.   
<br>

### Overfitting
Data augmentation and a special (optional) layer called the dropout help avoid **overfitting**:
<br>
<img src='https://drive.google.com/uc?id=1IR65_95QP5ov5L9Ha2k6FuHRfgQlAsio' height=400>


**Overfitting** is when the model gets super good (high accuracy, low loss) at classifying the training data as it completes multiple epochs, but gets really bad (low accuracy, high loss) when presented with test data. The model is essentially picking up on patterns in the test set that help it score well with training, but aren't actually useful in classifying pictures -- so then it fails to properly classify pictures in the test set, since it's relying on patterns that don't actually matter. The graph above is the flowers example without data augmentation and dropout.   

Possible real-life comparison: you review old homework problems as you study for an exam, and you get really good at solving those  problems over and over -- you get the process, you know how it all clicks, everything's dandy. But come exam day... well, those same questions aren't there on the exam (unless your professor is super nice, I guess). You don't do so hot. Why? *Because you got good at just the patterns in the practice questions, not the actual concept behind them!*

If you're curious about **dropout**, it randomly removes a certain portion of outputs from nodes to avoid the model from overfitting to spontaenous patterns. You can read more about it <a href="https://keras.io/api/layers/regularization_layers/dropout/#:~:text=The%20Dropout%20layer%20randomly%20sets,over%20all%20inputs%20is%20unchanged.">here</a>.



That's all for now! Again, this was a fairly broad explanation that left out a lot of the really awesome math that's involved. It should enough to help make sense of the code, but researching the math in the background is definitely worth it.