# Sentiment-Analysis-on-Financial-Tweets

This is a machine learning project that analyses the mood of financial tweets. 

Tweets are first obtained, preprocessed and then analysed using Vader and Hugging face (BERT) for a benchmark. Next, a SVM model is trained on the data to perform a similar analysis by labelling the text as either positive, negative or neutral

Features
Sentiment Analysis: Classifies financial news into positive, negative, or neutral categories.
Model Training: Support Vector Machine for classification
Data Tokenization: Utilizes SpaCy for optimized preprocessing
Evaluation: Provides training and validation accuracy to assess model performance.
Prediction: Offers functionality to predict sentiment for new text inputs.
Tech Stack
Programming Language: Python
Machine Learning Framework: Torch
Transformers Library: Hugging Face Transformers
Pre-trained Model: Vader, BERT
Data Processing: Pandas, NumPy
Evaluation: Scikit-learn
Data Loading: Torch DataLoader
