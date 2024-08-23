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
