Place the challenge_solved.ipynb in the same folder with the CTF challenge files.
Unzip test_X.zip contents to test_X folder

Running the script and computation takes several minutes on a good coputer. Be ready to wait.

Writeup:

We are presented with files:
- meta               # bytestream file that includes the labels for possible classifications
- model.py           # machine learning model description in python
- challenge.ipynb.   # notepad fyle including the foundation for the solution
- state_dict.pt      # trained model
- test_X.zip         # archive with 8192 pictures

The notepad contained a flag variable with size 256 x 32 which gave a hint that the pictures would make up an answer. The challenge inctroduction also said that we need to distinguish people from large man-made constructions.

First we declare the model, load the weights from state_dict.pt and set the model to evaluation mode.

Then we use for loops to run through the rows and colums of the flag, individually loading the images, pre-processing them using the function from the original challenge.ipynb and then converting the result to tensors.
Then we get a predicted class from the model. The images that are classified as "large man-made constructions" are coloring the pixel for the flag in white. The images that are classiffied as people will result in a black pixel.

The for loops take significant time to process and require several minutes on modern computers and might take a while on an older hardware to process.
