Original papers:
1) [Recurrent Chunking Mechanisms for Long-Text Machine Reading Comprehension](https://arxiv.org/abs/2005.08056)ACL Main 2020
2) [Post-Hoc Answer Attribution for Grounded and Trustworthy Long Document Comprehension: Task, Insights, and Challenges](https://aclanthology.org/2024.starsem-1.4/) \*SEM 2024

Long Document Comprehension (LDC) is a much desired skill in language models and is a requirement of some applied language models, such as in the legal domain (see [[Legal Case Retrieval]]). Where automatic QA systems are prone to producing misinformative answers and hallucinations, answer attribution could help improve confidence and explainability.  









## Answer Attribution
This is the process of attributing an answer to some reference text as to ground the answer in a source text. 

- **Attribution** The action of regarding something as being caused by a person or thing
- **Abstractive/Compositional Attributions:** An answer could be  composed of multiple sentences in the source document (2) 

The task of attribution could be posed as a textual entailment task, where sentences in the document are the premise and an information unit in the answer the hypothesis.


TODO:
(2) Review the datasets which they reformulate 