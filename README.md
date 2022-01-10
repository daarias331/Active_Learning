# Active_Learning

Most machine learning models are based on supervised learning, applied to a given training dataset which
includes instances and their labels. In many practical settings, however, labelled data is not readily available.
While unsupervised learning is one way of dealing with this situation, a popular alternative that can still make
use of powerful discriminative machine learning methods is Active Learning. This describes a machine learning
framework whereby data is labelled in an incremental manner, and a machine learning model is used to decide
what data instances should be annotated next. This allows the model to focus the labelling effort—which can
often be slow and expensive, e.g., requiring manual human labour—on highly informative instances which can
correct weaknesses in the model. There are several different strategies for choosing (or synthesising) data for
annotation, and this project will require you to understand and implement several such techniques.

I have  developed pool-based active learning methods to implement an active learning framework, and
used this to support uncertainty sampling and query by committee sampling.

I used the a part of the OmniGlot dataset to simulate active learning of a classifier which detects the language given a
handwritten character image. The dataset comprises the alphabets of 30 different languages,  with a total of 19,280 images of hand-drawn characters.  
The data can be found in the following files:

* images.npy: a matrix of 19,280 x 1,000 encoding images of handwritten characters, each embedded in 1000d
* labels.npy: a vector of 19,280 string valued labels, encoding to the alphabet name of the corresponding image

Sampling methods:
* Random Sampling: Select random samples to be queried
* Uncertainty Sampling:  This works by selecting instances that have the most predictive uncertainty under the model, and accordingly one
would expect the model to learn the most from their labelling.
* Query by comittee: it is based on training an ensemble of several models and measuring the extent
of disagreement within the ensemble as the selection heuristic. The idea is that instances that are predicted
differently by each ensemble member are likely to be highly informative, once labelled. I implemented 3 methods:
  * Vote entropy (or hard voting)
  * Soft entropy (or soft voting)
  * KL (Kullback-Leibler) divergence
