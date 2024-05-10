# Hypernym-Discovery
To predict ranked list of 15 candidate hypernyms for a target word


## Table of Content
  * [Demo](#demo)
  * [Overview](#overview)
  * [Goal](#goal)
  * [Technical Aspect](#technical-aspect)
  * [Results](#results)
  * [Technologies Used](#technologies-used)

## Demo
Result:  
![image](https://github.com/Sagnick0907/Hypernym-Discovery/assets/76872499/75dc1c44-bafb-4962-94ef-6a630296bb27)

## Overview  
The task of Hypernym Discovery in the paper is defined as finding and extracting suitable hypernyms for a target input term from a large textual corpus. For each input term the expected output is a ranked list of candidate hypernyms (up to 15) drawn from the provided vocabulary.  
We are provided with a target term, a source corpus, and a vocabulary, and are required to retrieve a ranked list of candidate hypernyms for the input term. The task is split into two subtasks, general-purpose hypernym discovery and domain-specific hypernym discovery. Each subtask features specific training testing and trial data containing input terms and corresponding gold hypernym lists to evaluate the performance of participating systems.

## Motivation and Goal  
This project helps enhance NLP tasks like question answering and semantic search by improving semantic understanding through hypernym discovery (Develop and evaluate algorithms for automatically extracting hypernyms from text, both in general-purpose and domain-specific contexts).  

## Technical Aspect  

We have proposed 4 methodologies for this project.  
- Baseline Method:  
   In our base-line strategy, we decided to divide our task into two key subtasks:
  - "Embedding learning" (using Word2vec).
  - Hypernym-hyponym relationship learning.
    In the supervised approach, we use neural network models (e.g., GRU and LSTM) to extract the latent representation of hyponym and hypernym embeddings. We then compute the similarity between eq (query's latent representation) and eh (corresponding hypernym's representation) using cosine similarity. The following approaches have been addressed in the literature and will serve as supervised baselines for our progress.  
- Projection Method:  
  A projection model in the context of neural networks is generally a part of the architecture that involves transforming input data (such as embeddings) into a new space. This transformation is typically achieved through linear layers (or matrices), which can project high-dimensional data into a lower or differently structured dimensional space.
- Exploiting Embedding Space:  
  - Define sense vectors as latent continuous representations of word senses from Word2Vec.
  - Cluster individual word embeddings into domain clusters using k-means clustering.
  - Generate lexical domain vectors by concatenating hypernyms within each cluster.
  - Compare lexical vectors with pre-trained domain vectors using Weighted Overlap (W_O) similarity measure.
  - Assign clusters to domains based on highest similarity scores, ensuring reliability with a similarity threshold.
  - Prepare data by creating pairs of hypernyms and their domains from domain-all_hypernym mappings.
  - Create hyponym and hypernym matrices composed of SenseEmbed vectors within each domain cluster.
  - Learn a transformation matrix for each domain cluster by minimizing a loss function that measures the difference between predicted and actual hypernym vectors.
  - Derive a ranked list of probable hypernyms for unseen terms using a cosine similarity measure.
  - Transform the hypernym discovery task into a ranking problem and extracted probable candidates using top-k filters.
- Transformers (Bert):  
  Data preparation: Contrastive pairs of data  
  Transformer Model used:   
  - bert-base-uncased for English (subtask 1A), Medical (subtask 2A) and Music (subtask 2B) datasets   
  - bert-base-multilingual-uncased for Italian (subtask 1B) and Spanish (subtask 1C).  
  Full fine-tuning on pre-trained BERT models on each language-specific dataset, leveraging the embedding representations learned by BERT to predict hypernyms.   
  This transfer learning approach enabled the models to capture language-specific semantic relationships and generalize to predict hypernyms across different domains.  


## Results  
![image](https://github.com/Sagnick0907/Hypernym-Discovery/assets/76872499/d64bd90b-5f4c-49d8-837b-c21daf7661d5)  
![image](https://github.com/Sagnick0907/Hypernym-Discovery/assets/76872499/d2c6e9c2-42b8-4278-883c-0c75ff93e91a)  
![image](https://github.com/Sagnick0907/Hypernym-Discovery/assets/76872499/a9916a54-8f09-446e-ad0e-478b56739628)  
![image](https://github.com/Sagnick0907/Hypernym-Discovery/assets/76872499/bc5eaeea-b62c-469b-a3eb-5a04a2251510)  
![image](https://github.com/Sagnick0907/Hypernym-Discovery/assets/76872499/bd51db40-88e5-473d-ae77-9aa79f178012)  



## Technologies Used
- VSCode
- Kaggle
- Google Colab
