In this challenge we're giventwo files:

- architecture.py
- bigram_model.pt

Googling .pt file extension I understood that it's a trained weights for a ML model. From an article we learn how to load that file to implement with a model (1).

From the python script we have a clue that the model is a "BigramLanguageModel". Googling that we find out that the model should be able to predict a character based on the previous input using the "forward" method.



(1) https://pytorch.org/tutorials/beginner/saving_loading_models.html