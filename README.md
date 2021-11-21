# Candidate-and-job-recommandation-software
This repository contains a juptyer notebook and the data source obtained from, Job Recommendation based on Job Seeker Skills: An Empirical Study conducted by Jorge Valverde-Rebaza, Ricardo Puma, Paul Bustios, and Nathalia C. Silva. Which contains 3 reviews made by 3 different recruiters. 

For each file the is candidate's area of expertise, background, and skills and the title and description of the job vacancy. The last column is the score (0-10) that the recruiter assigned to each candidate.

Please note the following to run the the jupyter notebook provided in the above you will need to download the glove (Pre-trained model.), the following link can be used, you will need to place the downloaded files in glove directory:

Link: https://drive.google.com/drive/folders/1d5sDW6ZaB0tFCcYAxj1VlCuZGNpL9bwr?usp=sharing


#### Data Preprocessing
For all Deep Learning models typically the is data pre-processing that is needed to ensure that only the relevant keywords are used when creating a model so as to reduce noise, to achieve this we performed some pre-processing on the CSV file to clean our data, we removed non-ASCII character in our dataset. Since the provided files we already structured we didn't need to do data scrapping which is typically need for unstructured data.

#### Feature Representation
<b>Firstly</b> we performed some data cleaning by implementing a function to remove non-ASCII characters from the dataset. After performing cleaning we combined the sentences from the candidate and job recommendation to create a dictionary of unique words that we have in our vocabulary. Since sentence size may vary we ensured that the sentence size is no large than 10000, and we took a maximum word length and pre-padded zeros to ensure that the representation is similar across a sentence with varying sentence length.

The <b>second</b> step, feature representation, aims to represent these documents (job offers and profiles) as vector space models. For this purpose, we adopted an approach: word embedding. From the variety of word embedding representations, we selected GloVe (Global Vectors for Word Representation) embedding model, we used a pre-trained model from Stanford University. With GloVe, you can obtain vector representations of words using unsupervised learning. Training is based on globally aggregated co-occurrence statistics from a corpus of words. The resulting vector representations show interesting linear substructures within the words.Were used the Glove nearest neighbor approach (or cosine similarity) in our model to make use of the semantic similarity between words. Were used a word vector for each sentence and an embedding matrix developed by using Glove weights.

For the <b>third</b> step we opted to use Long-term short-term memory (LSTM) rather than Recurrent Neural Network(RNN) because RNN suffers from the vanishing gradient problem, which means the algorithm does not remember the information initially used. In LSTMs, cell states are introduced as "highways" for the gradient to flow up and backward through time freely, thus making it more resistant to the vanishing gradient problem. Cell state is almost like data stored in the memory of a computer. An LSTM can "remember" or "forget" information about the current state of the cell through specialized neurons called "gates".
