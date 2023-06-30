# CNN Examples
Examples of Convolutional Neural Networks in action! 

### Running these notebooks locally
If you're running this locally, I recommend using a virtual environment, especially if you don't have libraries like tensorflow installed globally.   
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