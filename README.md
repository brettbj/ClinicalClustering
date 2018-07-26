Seq2Seq Dimensionality Reduction for Clinical Clustering
===========================================================

This repository contains code to perform dimensionality reduction of a variable length sequence and then cluster.

![](<./images/workflow.png>)


There are five main parts to this process:

  1. Preprocessing - Feature Selection, Construction and learning of distributed representations (embeddings).
      - Feature Selection - we currently include 3 settings - comorbidity, fact selection and sequences.
      - Construction
      - Learning of embeddings - Initially we show typical word2vec embeddings trained with a fixed window.
      - Future work includes dynamic bernoulli embeddings, hiearchical representations, context-based representations and
      - We perform two separate analyses -  include patient histories prior until 0-6 months (uniform) before diagnosis of disease, as well sep , include complete patient histories but exclude related diagnoses from training data.
      - For comparison we also build comorbidity matrices as well as fact summarization matrices


  2. Training the dimensionality reduction (variable to fixed length) model.
    - Architecture - We pass the input sequences to a seq2seq style model.


  3. Performing clustering
    - Traditional Clustering Techniques:
      - KMeans
      - Affinity Propagation
      - MeanShift
      - Spectral Clustering
      - Ward
      - Agglomerative Clustering
      - DBSCAN
      - Birch
      - Gaussian Mixture Models

    - Tested with different Dimensionality Reduction Methods
      - Seq2seq dimensionality reduction
      - PCA
      - UMAP

      ![](<./images/collection.png>)

  4. Evaluation
    - Held-out ICD9 codes - We measure enrichment of held-out labels (ICD9 codes) in identified clusters. The following metrics are computed on the clusters:
      -  Rand Index - what percentage of clustered occurrences agree (similar to mutual information)
      - Homogeneity - what percentage of a cluster is the dominant class?
      - Completeness - what percentage of a class goes to a specific cluster
      - V-Measure - 2 * (homogeneity * completeness) / (homogeneity + completeness)

  5. Analysis -
    - Latent space evaluation - we also look for meaningful transformations in the latent space by passing held out sequences in all of their combinations (in attempt to identify the effect of time) as well as passing in each sequence with the opposite gender attached.

Required
--------
- keras                              2.1.2
- pandas                             0.23.0
- numpy                              1.14.5
- scikit-learn                       0.19.1                   
- scipy                              1.1.0                    
- seaborn                            0.8.1    
- tensorflow-gpu                     1.4.1


Citation
--------
Coming Soon

References
--------
Keras

Feedback
--------

Please feel free to email me - (brett_beaulieu-jones) at hms.harvard.edu with any feedback or
raise a github issue with any comments or questions.

Acknowledgements
----------------

My work is supported by a T15 NLM Grant (4T15 LM007092-25) and funding from UCB. This repository was built while attending  Tensorflow Korea DL Jeju.
