# Genomic Sequence Analysis: Final Report

Purpose / Motivation: 
Analyzing genomic data at scale presents significant computational challenges due to the size of DNA sequences, which can contain millions to billions of nucleotide bases. Naive string search methods that compare patterns character by character quickly become infeasible at this scale because of their high time complexity.
The purpose of this project is to explore how machine learning models can be applied to genomic sequence data by treating DNA as structured, text-like input. Algorithmic preprocessing techniques are used to convert raw biological data into forms that enable model training, evaluation, and comparison.
Project Goals:
Develop and evaluate baseline machine learning models for analyzing genomic sequence data, including a neural network model and a logistic regression classifier.
Investigate different feature representations for DNA sequences, such as one-hot encoded bases, and assess how these representations affect model performance.
Apply standard AI evaluation practices, including train–test splitting and performance metrics, to measure model generalization and compare approaches.
Use preprocessing techniques (FASTA parsing, nucleotide encoding, and Burrows–Wheeler Transform construction) to support and inform model design, rather than as standalone outcomes.

Scope of the Project:
Preparing genomic sequence data for learning based analysis through parsing and encoding. Implementing and evaluating baseline machine learning models:
A feedforward neural network.
Logistic regression using Bag of Words and TF–IDF features.
Comparing model behavior and performance using standard evaluation metrics.
Relation to AI Concepts Learned in Class:
	Techniques from natural language processing, including Bag of Words and Term Frequency–Inverse Document Frequency, were used to convert nucleotide sequences into numerical feature vectors. Character level n grams were employed to capture local sequence patterns, reflecting how short character groupings are used in text analysis. Logistic regression was used as a baseline classifier, providing an interpretable linear model against which learning performance could be evaluated.
	Baseline machine learning models were implemented and evaluated to examine how different feature representations affect performance on genomic data. A standard train test split was used to assess model generalization, ensuring that evaluation metrics reflected performance on unseen data rather than memorization of the training set.
Related Work:
Logistic regression for the classification of genetic sequences
(https://www.biorxiv.org/content/10.1101/2022.08.15.503907v1) 
Authors: Michael A. Zeller, Zebulun W. Arendsee, Gavin J.D. Smith, Tavis K. Anderson
	This work influenced our approach by demonstrating that logistic regression can serve as an effective and interpretable classifier for biological sequence data when combined with appropriate feature representations.
DNA Sequencing using Machine Learning and Deep Learning Algorithms
(https://www.ijitee.org/wp-content/uploads/papers/v11i10/J927309111022.pdf) 
Authors: Varada Venkata Sai Dileep, Navuduru Rishitha, Rakesh Gummadi, Natarajan P
This paper influenced our approach by demonstrating that DNA sequences can be effectively represented using fixed length k mer features and analyzed with standard machine learning classifiers.
Kahn, E. "Natural language processing, big data, bioinformatics and biology." Int. J. Biol. Biomed. Eng 8 (2014): 107-117.
This paper concentrates on how NLPs can be used in conjunction with the massive datasets of genetic sequences. It specifically mentions how NLPs may lack the power to determine genetic expression due to the level of context required in bioinformatics. It then details how an AI may create a context and semantics based approach to improve the accuracy and precision of these agents. 
Dataset and Preprocessing:
The datasets used in this project were obtained from the National Center for Biotechnology Information (NCBI), a public repository widely used for genomic and biological research. The data consisted of nucleotide sequences provided in FASTA format, including a reference sequence for human chromosome 15 and a sequence associated with oculocutaneous albinism. FASTA was chosen because it is a standard form for representing long DNA sequences and is directly supported by common bioinformatics libraries.
To construct a dataset suitable for supervised learning, the sequences were segmented into fixed-length substrings. Each sample corresponds to a short contiguous segment of DNA, allowing all examples to share a uniform structure. Labels were assigned to match the number of generated segments, resulting in a balanced dataset.
Before feature extraction, basic data cleaning and validation steps were applied to ensure consistency across the dataset. Any characters outside the standard nucleotide bases were removed. The FASTA files were validated by printing fixed-length subsequences to confirm correct parsing. After feature construction, the dataset was randomly shuffled to remove ordering effects before being split into training and testing subsets for model evaluation. Visualizations of these processes can be found in the .pynb files submitted along with this report. 
Algorithms and Methods: Explain the AI algorithms used and why they were selected.
Neural Network: We utilized a neural network qualified by TF-IDF and BoW. BoW was used to determine the amount of respective nucleotides. If a certain nucleotide occurs a certain amount, that could indicate a certain gene expressing itself. The initial thought process was that the BoW model with ngrams, could be useful in designating specific k-mers within a genetic sequence as they are both specific lengths of non-contextual characters. TF-IDF may be more explicitly useful in this circumstance as it will reduce the amount of computational power required as well as allowing us to quickly parse through all of our data.
Results and Evaluation: Present metrics, tables, and graphs comparing models and tuning choices.

Figure a.) Graphical representation of accuracy of the models when utilizing BoW vs TF-IDF


Discussion and Analysis: Interpret performance and limitations.


TF-IDF and BoW seem to be poor choices for our purposes as they were only able to detect if a segment had albinism roughly 40-50% of the time. This is most likely due to a few reasons relating to issues of context based locations and lack of any real “language” in a sense.
In terms of BoW some issues that it may have run into are the issues of context. An issue that may interact with the agent is how genomic sequences are context dependent. This means that if even a specific nucleotide in a specific place can change if a gene expresses or not. Additionally since there are no real “words” for the model to recognize this limits its effectiveness. However the information it gives on the amount of specific nucleotides does provide some useful information for the agent. Working on if there are more specific nucleotides in the sequence the agent uses that to determine if a gene is expressed. 
In terms of TF-IDF the idea of using k-mers to our advantage and using them as a basis for ngrams. This helps to reduce the amount of computational burden on the system by allowing detection of these k-mers to help break up the extremely long sequences of characters. 
Conclusion and Future Work: 
In conclusion, our analysis of Chromosome 15 successfully showed us that machine learning can distinguish genomic sequences associated with Albinism. Furthermore, our Neural Network has the best performance which achieves 100% accuracy and identifies complex and nonlinear relationships.
This project could be expanded to include a library of known genetic conditions on a specific chromosome rather than just one singular gene. Further research into how we can maximize the effectiveness of the ngram and k-mer interaction
