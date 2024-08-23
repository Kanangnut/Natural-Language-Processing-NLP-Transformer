This project implements a Transformer model based on the "Attention Is All You Need" paper for a translation task using the European Parliament Proceedings Parallel Corpus. Here's a summary of each stage:

### Stage 1: Importing Dependencies
- **Purpose**: To set up the necessary libraries and modules.
- **Actions**: 
  - Import Python libraries such as NumPy, TensorFlow, and TensorFlow Datasets.
  - Install TensorFlow and TensorFlow Datasets if needed.

### Stage 2: Data Preprocessing
- **Loading Files**:
  - Import text files containing parallel corpora in English and Spanish, as well as non-breaking prefixes.
  
- **Cleaning Data**:
  - Process the corpora to manage punctuation and spacing issues.
  - Replace and remove certain punctuations and clean multiple spaces.
  
- **Tokenizing Text**:
  - Convert text into numerical tokens using `SubwordTextEncoder` from TensorFlow Datasets.
  - Define vocabulary size and encode sentences.
  
- **Removing Long Sentences**:
  - Filter out sentences longer than a specified maximum length to ensure uniformity in training data.
  
- **Inputs/Outputs Creation**:
  - Pad sequences to a uniform length and create TensorFlow datasets for model training.
  - Prepare the data for batching and prefetching to optimize performance.

### Stage 3: Model Building
- **Positional Encoding**:
  - Implement a layer to encode the positions of tokens in the sequence using sine and cosine functions.

- **Attention Mechanism**:
  - Implement scaled dot-product attention and multi-head attention layers.
  - Multi-head attention splits inputs into multiple projections to capture different aspects of relationships between tokens.

- **Encoder**:
  - Construct the encoder with layers of multi-head attention and feed-forward networks, incorporating positional encoding and dropout for regularization.

- **Decoder**:
  - Build the decoder with similar layers to the encoder but with additional attention to the encoder's outputs.
  - Handle masking to manage padding and look-ahead within sequences.

- **Transformer Model**:
  - Combine the encoder and decoder into a complete Transformer model.
  - Implement methods to create padding and look-ahead masks to manage sequence lengths and prevent future token peeking during training.

This setup provides a robust framework for machine translation, leveraging the Transformer architecture to handle sequential data effectively.

In this project, the tools and technical solutions used are:

### Tools
1. **Python**: Programming language used for implementing the project.
2. **TensorFlow**: Open-source deep learning framework for building and training the Transformer model.
3. **TensorFlow Datasets (TFDS)**: Library used to handle and preprocess text data.
4. **NumPy**: Library for numerical operations and array manipulations.
5. **Jupyter Notebook**: Development environment for writing and executing Python code.

### Technical Solutions
1. **Transformer Architecture**:
   - **Positional Encoding**: Adds positional information to input embeddings to capture the order of tokens.
   - **Multi-Head Attention**: Allows the model to focus on different parts of the input sequence simultaneously.
   - **Scaled Dot-Product Attention**: Computes attention scores by scaling dot products of queries and keys.
   - **Encoder-Decoder Structure**: Uses an encoder to process the input sequence and a decoder to generate the output sequence.

2. **Data Preprocessing**:
   - **Text Tokenization**: Converts words into numerical tokens using `SubwordTextEncoder` to handle vocabulary and improve model performance.
   - **Data Cleaning**: Removes unnecessary characters, handles non-breaking prefixes, and tokenizes the text.
   - **Padding and Truncation**: Ensures all sequences have the same length for batch processing.

3. **Model Training**:
   - **Dataset Preparation**: Uses TensorFlow's `tf.data.Dataset` for efficient batching, shuffling, and prefetching of data.
   - **Training Configuration**: Implements training with dropout for regularization and masks to handle padding and future tokens.

4. **Masking**:
   - **Padding Mask**: Prevents the model from attending to padding tokens.
   - **Look-Ahead Mask**: Ensures that the decoder does not attend to future tokens during training.

