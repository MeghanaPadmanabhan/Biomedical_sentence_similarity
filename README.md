# Biomedical_sentence_similarity
This repository discusses sentence level similarity to capture the best biomedical category that a given sentence falls into in the context of text-related search.
<br>
We move from Simpler ideas using already pretrained models to more complex specialised biomedical models that can solve this specialized biomedical text-related search problem.
<br>
We discuss papers in the chronological order of models tried
<br>
<a href='https://arxiv.org/pdf/1803.11175.pdf'>Universal Sentence Encoder</a><br>
Applies trasfer learning to obtain sentence level embedding. Obtains respectable performance with minimal fine-tuning for supervised learning task. The model toolkit consists of two new models that can be used to obtain sentence level encodings, one makes use of transformer models while the other makes use of the Deep Averaging Network (DANs) for the same. The models can generate the sentece embedding directly when an input sentence is given. But when used with a larger model, it can be fine-tuned using gradient-based updates for our specific task. The two encoding architectures, the Transformers and the DANs are discussed in brief:
<ul>
  <li> <b>Transformer based encoders: </b> This architecture uses context-aware representations of words in a sentence that takes into account both the ordering and identity of other words in a sentence. Each word in a sentence is converted to a fixed-length vecor and the sentence embedding is the element-wise summation of the word vectors in the snetence. The model is trained on multiple downstream tasks (multitask learning), SkipThought like task for unsupervised learning from arbitrary text, conversational input-response task, supervised data classification task. This model performs well on the embedding tasks at the cost of higher compute power, resource and time which scales up with increased sentence length. 
  </li>
  <li> <b>DANs: </b> With DANs, the word and bi-gram embeddings are averaged and passed through a Deep Meural Netowrk (DNN) to get the final sentence embedding. The tasks trained on are similar as the transformer model, but the advantage of using DANs is that the training time is failrly linear to the length of the input sentence. </li>
  </ul>
  <br>
  <b> Training data: </b>
  <br>
  Unsupervised tasks are trained using resources from several sources like wikipedia, web question anser websites. Augmenting this unsupervised task with supervised training using  Stanford Natural Language Inference (SNLI) corpus is shown to improve performance. Several popular datasets are used for further training: MR (movie review dataset), CR (Customer review dataset), SUBJ (subjectivity of sentences from movie reviews), MPQA (news data), TREC (question classification data), SST (Binary phase level sentence classification), STS Benchmark (Semantic textual similarity marked by humans on a task), WEAT (word pairs from psycology literature that is used to characterize model bias). 
  <br>
  <b> How are the pre-trained models fine-tuned for the sentence similarity task that we have in hand?</b>
<b> Results of using the generic sentenve embeddings on biomedical text (without fine-tuning): </b> Check out USE_on_generic_text.ipynb for results. 

<br>
<a href='https://arxiv.org/ftp/arxiv/papers/1810/1810.09302.pdf'> BioSentVec: creating sentence embeddings for biomedical texts </a>
<br>
BioSentVec is a model trained with over 30 million documents from both scholarly articles in PubMed and clinical notes in the MIMICIII Clinical Database. The authors evaluate BioSentVec embeddings in two sentence pair similarity tasks in different biomedical text genres, which is likely suitable to our task.
The bioSentVec is created using the sent2vec model, which makes use of the model to compute the 700-dimensional sentence embeddings. Evaluation is performed on clinical sentence similarity task, using BIOSSES and MedSTS datasets.


  
