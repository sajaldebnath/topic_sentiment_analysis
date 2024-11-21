## **IISc - CCE AI/ML Capstone Project - Topic Modeling and Sentiment Analysis of User Reviews**

### **Abstract:**

This project is divided into two main phases. The first phase involves analyzing user reviews to identify key topics within the data. In the second phase, sentiments are assessed for each identified topic, aligning reviews with their corresponding topics and sentiment categories. 

### **Approach:**

1. **Topic Modeling**

There are multiple ways to do topic modeling. For example, 

* **Term Frequency-Inverse Document Frequency (TF-IDF)**: A technique in natural language processing where the TF-IDF weighting scheme is used to identify important words within a corpus of documents, allowing for the extraction of key themes and topics across the collection

* **Latent Dirichlet Allocation (LDA)**: Considered the gold standard, it uses a probabilistic framework based on Dirichlet distributions to model how topics are distributed within documents and words within topics.

* **Latent Semantic Analysis (LSA)**: A foundational technique that uses singular value decomposition (SVD) to identify latent semantic relationships between words in a corpus.

* **Non-negative Matrix Factorization (NMF)**: A matrix factorization method that ensures all components (topics and words) are non-negative, often preferred for interpretability.

* **Probabilistic Latent Semantic Analysis (pLSA)**: Similar to LSA but with a probabilistic model, offering better theoretical grounding.


**Why Use LDA?**

* **Unsupervised Approach**: You don’t need labeled data.

* **Scalable**: It works for small and large datasets alike.

* **Insightful**: Helps discover hidden themes in data without manual effort.

**When to Use LDA**

LDA is ideal for tasks like:
* Analyzing reviews to extract common feedback topics.

* Summarizing themes in a large set of articles.

* Organizing unstructured text data for further analysis.

Since I am working on user reviews dataset, I am using LDA as it is easier to implement and provides fairly accurate result.


2. **Sentiment Analysis**:

Two of the most used libraries for this purpose are **TextBlob** and **VADER**.
While both TextBlob and VADER are used for sentiment analysis, the key difference is that **VADER is specifically optimized for social media text**, meaning it handles slang, emojis, and other features common on platforms like Twitter better than **TextBlob, which is more general-purpose** and simpler to use for basic sentiment analysis. 

** Key points about TextBlob and VADER**
* **Focus**:
TextBlob is a more general sentiment analysis tool, while VADER is specifically designed for social media text.

* **Strengths**:
VADER excels at interpreting social media slang and punctuation, including emojis, while TextBlob is considered easier to implement and understand for basic sentiment analysis.

* **Accuracy**:
Depending on the data, VADER might provide a more accurate sentiment analysis for social media content due to its specialized lexicon. 

**When to use TextBlob**: 
  * Simple sentiment analysis tasks where context is not critical 
  * General text analysis where social media features are not prevalent 

**When to use VADER**:

  * Analyzing sentiment on social media platforms like Twitter or Facebook
  * Cases where understanding slang, emojis, and capitalization is important


Since I will be using topic modeling using **LDA model** and then use **NLTK Vader library** to do sentiment analysis. The next step is to find out the accuracy of the model. I will be using the Coherence score to determine the accuracy. There are other methods which I will detail while going through each section.

#### **What is LDA**

* **What is Latent Dirichlet Allocation (LDA)?**

LDA is a probabilistic method used in topic modeling that helps in identifying hidden themes or topics in a collection of text documents. It assumes that each document is made up of multiple topics, and each topic is made up of certain words that frequently occur together. Also, each word in the document can be attributed to one of these topics.

Rather than manually labeling data, LDA automatically uncovers these patterns, making it useful for tasks like analyzing reviews, news articles, or any text data.

* **How Does LDA Work?**

We can consider LDA as a reverse-engineering tool for text. For example, while reading a book and trying to guess the following about the book:
  * What themes are being discussed (e.g., politics, travel, sports)?
	*	How much or what percentage of the book is focused on each of these themes?

**LDA does this mathematically by:**

* Breaking documents into small units (words).
* Determining:
  * Which “topics” are present in a document?
  * Which words are common for those topics?

**The Generative Process of LDA**

Here's how LDA imagines text is generated:
* Step 1: Pick a mix of topics for the document.
  * For example, one document might be 70% about “Food” and 30% about “Travel.”
* Step 2: For each word in the document:
  * Randomly select a topic based on the document's topic mix.
  * From the chosen topic, pick a word based on its relevance to that topic.

By observing actual documents and reversing this process, LDA figures out:

* The topic proportions for each document.
* The important words for each topic.

**Core Components of LDA**

* **Topics**: These are clusters of related words. For example:
  * Topic 1: hotel, room, breakfast, stay.
  * Topic 2: flight, airport, luggage, travel.

* **Topic Distribution**: Each document is a mix of topics. For instance:
  * A review might be 60% about “Hotels” and 40% about “Flights.”

* **Word Distribution**: Each topic has its distribution of related words, making some words more likely to appear in that topic.

**LDA in Simple Terms**

For example, let's consider sorting 1,000 reviews into several categories without knowing their content beforehand. LDA looks at the words in each review and groups them into categories (topics) based on patterns. Reviews using similar sets of words will likely belong to the same topic.

For instance:

* Reviews with words like “beach,” “view,” and “sand” might fall under the topic “Vacation.”

* Those with “bed,” “clean,” and “bathroom” could belong to “Accommodation.”

**Evaluation of LDA**

1. **Topic Coherence**: Evaluate how meaningful the topics are.
2. **Model Perplexity**: Tests how well the model predicts unseen text.


**Challenges**

1. **Overlapping Words**: Some words may belong to multiple topics, making interpretation tricky.

2. **Preprocessing Dependency**: Noisy or unclean text can affect the quality of topics.

3. **Choosing the Number of Topics**: Deciding how many topics (a key parameter) to generate is not straightforward.

**Methods of Implementation**

* Manual Implementation
* Using libraries like the following:
  * Gensim
  * Sklearn (scikit-learn)

While Gensim is the more prevalent method, I chose **scikit-learn** library because it was faster to run in my environment and dataset.

#### **Process**
The main implementation steps are defined below. I will provide more details as I go through them.

1. **Data Loading and Preprocessing**: Read the data, clean it, and prepare it for topic modeling.

2. **LDA Modeling with Sklearn**: Use Latent Dirichlet Allocation to discover topics.

3. **Sentiment Analysis**: Assign sentiment polarity to the reviews for each topic.

4. **Visualization**: Create colorful graphs representing topics and sentiments.

5. **Evaluate Effectiveness**: Use coherence scores for evaluation.

6. **Hypertuning Parameters**: Suggest methods to improve the model.
