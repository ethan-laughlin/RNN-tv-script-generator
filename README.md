# RNN TV Script Generator Project

Recurrent Neural Network (RNN) defined and train to generate new tv scripts - in this case Seinfeld scripts. This project was completed as part of Udacity's Deep Learning Nanodegree program.

# Project Overview
This project focuses on creating a RNN in PyTorch that can learn to generate new tv scripts - like Seinfeld scripts.

## Notebook Sections
1. Load in Dataset
2. Explore Dataset
3. Preprocess Dataset: Lookup Tables, Tokenize Punctuation, Save Preprocessed data
4. Batch Data & Create Dataloader
5. Define Recurrent Neural Network (RNN) Architecture
6. Define Forward & Backward Propagation
7. Define Training Function
8. Set Model Hyperparamters
9. Train RNN & Save Model
10. Generate New Scripts 

# Results
The model generates conversations between the characters based on the first keyword provided. The script isn't perfect but can be a bit amusing. Common issues seen: duplicated words in a single line, mixing spoken lines with (stage directions), and excessive punctuation. 

## Example Script Output:
<img src="./example_output_4.png">

# HyperParameters Set
- Sequence Length: 50
- Training Epochs: 40
- Learning Rate: 0.001
- Embedding Dimension: 1000
- Hidden Dimension: 256
- Number of Layers: 2

## Determining Hyperparameters
1) **Sequence Length**: I chose a sequence length of 50 to give the network a context of approximately 10 script lines on average to consider during training. This was derived from the fact that the average number of words per line was 5.5. Mode of thought: The more context the network could learn from while maintaining efficient training, the better.

2) **Epochs**: I started out with 10 epochs as a first trial run to make sure the network would train and increased it to 20 thereafter. With 20 epochs the training loss settled around 2.2 which passed the initial requirement of less than 3.5; however, it was clear that the network could go even lower so I doubled the number of epochs to 40. At this point the loss further decrease but was starting to struggle to decrease consistently. Final training loss converged around 0.9.

3) **Batch Size**: Initially started with 256 as an arbitrary start point. Saw that the network was training efficiently but wanted to increase the number of batches being trained from per epoch so I cut this in half to 128. Network continued to train efficiently with no GPU memory issues encountered.

4) **Embedding Dimension**: Considered that the vocab contained ~46,367 unique words and cut this down significantly by 98% to 1000 embeddings.

5) **Hidden Dimension**: Chose 256 hidden dimensions to give the network a solid amount of features/states to learn from. Based on examples seen during coursework.

6) **n_layers**: Chose 2 layers since research covered in coursework states 2 layers is often better than 1 but 3 layers may or may not be better than 2. Additionaly, 3 layers would have added additional complexity to the network and unnecessarily slowed down training.

7) **Learning Rate**: Started with the default ADAM Optimizer learning rate of 0.001 and determined that it was sufficient to maintain efficient training.