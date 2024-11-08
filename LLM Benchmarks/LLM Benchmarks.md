LLM Benchmarks offer a set of standardised tests designed to evaluate the performance of LLMs on various skills, such as reasoning and comprehension. Specific metrics are used to quantitatively measure these abilities. These may range from statistics-based measures, such as the proportion of exact matches, to more intricate metrics evaluated by other LLMs.

## Static vs Dynamic/Live
Easier to apply static benchmarks to compare across multiple models, but risk of contamination over time is high

Dynamic is difficult to repeat in changing environments but less likely to be contaminated. 

## Evaluation Metrics

### Similarity Scores
- [[BLEu]] uses modified n-gram precision to measure how close a generated sentence is to expected output
	- Ground Truth in the sense that it requires an expected output so no good on generation but great for translation tasks
	- Lots of spins offs: 
		- [[ROUGE]] is recall oriented and is better for summarisation tasks
		- [[METEOR]] synonym/stem matching, with weighted F-score, good for Translation/Paraphrasing 
		- [[CIDEr]] TF-IDF weighting for n-grams, image captioning
		- [[SPICE]] Semantic graph matching, image captioning 
- [[BERTScore]] uses cosign similarity of embeddings to measure closeness to an expected output
	- Improves on some aspects of BLEu particularly semantic sensitivity and contextual understanding, but less interpretable and introduces bias
## Ground Truth
- [[HellaSwag]]
- [[MMLU]]
- [[LLM Benchmarks/Benchmarks/GSM-8K|GSM-8K]]

## Reference-free Metrics
- [[CLIPScore]]
- [[PAC-S]]
- [[UMIC (Unreferenced Metric for Image Captioning)]] 
## Human Preference


## LLM as a Judge


## Example Benchmarks
1) **Reasoning and Commonsense:**
	- [[HellaSwag|HellaSwag]]
	- [[BBH|BBH]]
2) **Language Understanding and Question Answering (QA):**
	- [[TruthfulQA|TruthfulQA]]
	- [[MMLU|MMLU]]
3) **Coding:**
	- [[Chatbot Arena|Chabot Arena]]
	- [[MT Bench|MT Bench]]
4) **Conversation and Chatbots:**
	- [[Chatbot Arena|Chabot Arena]]
	- [[MT Bench|MT Bench]]
5) **Translation:**
	- [[Chatbot Arena|Chabot Arena]]
	- [[BLEu|BLEu]]
6) **Mathematics:**
	- [[Chatbot Arena|Chabot Arena]]
	- [[MT Bench|MT Bench]]
7) **Logic:**
	- [[Chatbot Arena|Chabot Arena]]
	- [[MT Bench|MT Bench]]
8) **Standardised Tests (SATs etc)**:
	- [[Chatbot Arena|Chabot Arena]]
	- [[MT Bench|MT Bench]]

# Multi-Agent Benchmarks
