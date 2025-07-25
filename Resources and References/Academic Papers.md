In using an embedding model to compare the similarity of text gener
## Large Language Models (LLMs)

## Embeddings
- [T-FREE: Tokenizer-Free Generative LLMs via Sparse Representations for Memory-Efficient Embeddings](https://www.semanticscholar.org/reader/efc8e68d9a0d002141c49cf0101678880621132c)
	- Trigram tokenisation addresses large and growing vocab size of models upwards of 250k+ tokens

## Benchmarking
- [An Examination of the Robustness of Reference-Free Image Captioning Evaluation Metrics](https://aclanthology.org/2024.findings-eacl.14/)
	- KT: 
		- Looks at reference free image captioning evaluation metrics ([[CLIPScore]], [[UMIC (Unreferenced Metric for Image Captioning)]], [[PAC-S]]). Whilst having a high correlation with human judgement, they still struggle to identify fine-grained errors. **'All metrics fail to distinguish between correct and incorrect captions ~46% of the time.'**
	- Methods:
		- Convert [[VQAv2]] Dataset to a captioning dataset using [[GPT-J]] - motivated by the limitations of existing datasets where words are shuffled or swapped to create incorrect captions which are usually out-of-distribution and therefore easy to predict.
- [Are LLMs good at structured outputs? A benchmark for evaluating structured output capabilities in LLMs](https://www.sciencedirect.com/science/article/pii/S0306457324001687?casa_token=bbPRl_8zyDkAAAAA:PNjkDcjOy_XaPQs2FGJkazxAO5axMfmu3qNUkG98uPV3ji_iBFxTOQrvERbbhKbhEDT3H2-F)
	- KT: 
		- Evaluates the structured output capabilities of LLMs by introducing the [[SoEval]] benchmark.
	- Novel Ideas:
	- Methods:
	- Potential Cheats:
		- Uses GPT4 to create dataset, GPT4 achieves the best score across the benchmark
	- Usefulness to me:
	- Fallout Questions:
		- How can a benchmark like this be more fair? 
- [ZebraLogic: On the Scaling Limits of LLMs for Logical Reasoning](http://arxiv.org/abs/2502.01100)
	- KT:
		- Creates a dataset of [[Constraint Satisfaction Problems]] (CSP) to benchmark logical reasoning
		- Finds a 'Curse of Complexity for reasoning' - Performance dramatically declines as the problem complexity increases. As complexity grows, the limited reasoning in current LLMs are not solely a matter of model or sample size scaling.
		- Models with reasoning perform better due to hidden CoT tokens, but there is a limit to scaling in o1.
	- Novel Ideas:
		- Novel dataset that can be programatically expanded, is NP-complete, verifiable, and scales in difficulty for logical reasoning
	- Methods:
		- Generates dataset of logical grid puzzles
		- benchmarks various models on dataset, tests scaling model size, and test time compute to see what helps models to reason logically
	- Potential Cheats:
		- While clue generation is robust and paper is thorough in its investigation, different types of logical clues give different amounts of information i.e. `Peter FoundAT House x` carries more information than `Peter NotAt House x` 
	- Usefulness to me:
		- Interesting to see what the answer format adds/detracts from the reasoning process
		- Do their findings generalise across logic puzzles?
		- Can multi-agents make further improvements?
		- 
	- Questions:
		- `models may rely heavily on probabilistic correlations rather than genuinely understanding logical rules.` - How good are models at generating logical rules for a theorem prover? 
## Prompting Strategy 
-  [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)
- [Can Large Language Models Transform Computational Social Science](https://aclanthology.org/2024.cl-1.8.pdf)
	- Key Takeaways:
	- Novel Ideas:
	- Methods:
	- Potential Cheats:
	- Usefulness to me:
		- Great table of [[Effective Prompt Guidelines]]
	- Fallout Questions:
		- Review the citations of effective prompt guidelines

## Reasoning Models
- [Arithmetic Reasoning with LLM: Prolog Generation & Permutation](https://aclanthology.org/2024.naacl-short.61/) NAACL 2024
	- Key Takeaways: 
		- Prolog code generation is consistently better than CoT on [[GSM-8K]] 
		- Another win for intermediate representations for reasoning. Producing code that can be interpreted deterministically to produce an answer as appose to LLM guessing.
	- Novel Ideas:
	- Methods:
		- Converted the GSM8K dataset from CoT to Prolog code
		- Augmented the dataset by reordering Prolog code
		- Finetuned models on the dataset
	- Potential Cheats:
		- Corpus is 8.5k, test set only 1.3k, "Only considered samples with an integer answer" so how big was the test set in the end?
	- Usefulness to me:
		- Indicates that intermediate representations are useful in reasoning
		- First time seeing beam search being used, is this a sensible approach for code generation?
	- Fallout questions:
		- How large was the corpus after removing the non-integer samples?
		- What does permutation ratios refer to? 
## Multi-agent LLMs
- [Rethinking the Bounds of LLM Reasoning: Are Multi-Agent Discussions the Key?](https://arxiv.org/pdf/2402.18272)
	- Sceptic perspective of multi-agents performance over single agent 
- [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)
	- Key Takeaways:
	- Novel Ideas:
	- Methods:
	- Potential Cheats:
	- Usefulness to me:
	- Fallout questions
- [Personalised Abstractive Summarisation by Tri-agent Generation Pipeline](https://aclanthology.org/2024.findings-eacl.39/)
	- Key Takeaways:
- [Large Language Model based Multi-Agents: A Survey of Progress and Challenges](https://arxiv.org/abs/2402.01680)
- - [LLM-based Multi-Agent Reinforcement Learning: Current and Future Directions](https://arxiv.org/abs/2405.11106)
	- With LLMs, designing MARL frameworks becomes more analogous to modeling the group learning process of animals or even humans, where knowledge is transferred or exchanged via natural languages.
- [Dynamic LLM-Powered Agent Network for Task-Oriented Agent Collaboration - 2024](http://arxiv.org/abs/2310.02170)
	- Key Takeaways:
	- Novel Ideas:
		- T-FNN to organise agent communication in multi-agent
		- Early stopping using Byzantine Consensus theory
	- Methods:
	- Concerns/weaknesses:
		- LLM-based pairwise evaluations - prone to bias, inconsistent, interpretability
		- System relies on LLMs for everything - should a human be in the loop? 
		- Overcompliction - is is neccesary to make a full forward pass across x agents to assert which ones are best for the task? 
	- Usefulness to me:
	- Fallout Questions:
### Multi-agent VLMs
- [LLMs are Visual Reasoning Coordinators](https://proceedings.neurips.cc/paper_files/paper/2023/file/ddfe6bae7b869e819f842753009b94ad-Paper-Conference.pdf)
	- coodinative language model for visual reasoning proposed. Utilises a language model as a coordinator between multiple vision-language models to integrate their respective strengths for visual reasoning
	- Presented at NeurIPS 2023
	- Ablation study indicates that 'plausible answers' from VLMs help LLM answer visual reasoning questions

### Multi-agent Benchmarking
- [VillagerAgent](https://aclanthology.org/2024.findings-acl.964/)
	- Notes for presenting:
		- Looks to address the need for benchmarking collaborative agents in communication, planning, and reasoning skills in a dynamic environment
			- task specific challenges include resource allocation, task decomposition, and coordination. 
			- Construction task - understanding task requirements and planning work loads
			- Farm-to-Table - complex causal dependencies in a dynamic environment
			- Escape Room - Ability to execute tasks sequentially and in parallel
		- 
	- Key Takeaways:
		- Table 2 suggests diverse abilities (specialists) lead to bottlenecks and task failure due to increased complexity. 
		- Some indication of economies of scale with number of base agents for a given task
	- Novel Ideas:
		-  New benchmark: VillagerBench within minecraft environment claiming to test workload distribution, dynamic adaptation, & synchronised task execution.
			- Metrics: Completion, Efficiency, & Balance (distribution of workload among agents, higher = more equitable assignment), Block Placement View Hit Rate (VHR)
			- Tasks:
				- Construction Cooperation Task: Interpretation & Allocation
				- Farm to Table Cooking Task: Environmental Variability and Strategic Flexibility
				- Escape Room Challenge Task: Synchronisation and Sequential Execution
		- Directed Acyclic Graph Multi-Agent: VillagerAgent
			- Comprised of a Task Decomposer, Agent Controller, State Manager, and Base Agents.
			- Decomposer generates DAG of subtask nodes each round, Agent Controller assigns the subtasks to Base Agents, & State Manager maintains status of both environment and agents
	- Methods:
		- 100 Construction tasks, 100 Farm to table tasks, 25 escape room task all executed once
		- 
	- Potential Cheats:
		- What are the completion indicators?
	- Usefulness to me:
		-  sdas
	- Fall out questions:
		- How does competition effect groups of multi-agents?
		- Truly complex systems require experts across disciplines, what methods can be used to support expert base agents in this and other benchmarks?
		- Should we assess individual models as individual components? Frankenstein multi agents?
		- Do base agents incorporate image? how is the feedback generated?
- [Benchmark Self-Evolving: A Multi-Agent Framework for Dynamic LLM Evaluation](https://arxiv.org/abs/2402.11443)
- [AgentQuest: A Modular Benchmark Framework to Measure Progress and Improve LLM Agents](https://arxiv.org/abs/2404.06411)

- []()
- []()
- []()
- []()

## Applied LLMs
- [Large Language Models Offer an Alternative to the Traditional Approach of Topic Modelling](https://arxiv.org/abs/2403.16248)
- [CapsKG: Enabling Continual Knowledge Integration in Language Models for Automatic Knowledge Graph Completion](https://iswc2023.semanticweb.org/wp-content/uploads/2023/11/142650609.pdf)
	- Key Takeaway:
		- Catastrophic forgetting in KG generation via LMs can be avoided by using [[Capsules]] & [[Adaptors]] often utilised in [[Multi-task Learning]] and [[Continuous Learning]] strategies
	- Usefulness to me:
		- 

## Architectures
### Transformers


### Alternative Architectures
- [Were RNNs All We Needed?]([https://arxiv.org/abs/2410.01201](https://arxiv.org/abs/2410.01201))
	- Key Takeaway:
		- Proposes a faster architecture adapting RNNs to rival transformers quadratic time complexity. 
## Knowledge Retrieval
- [From Local to Global: A Graph RAG Approach to Query-Focused Summarization](https://arxiv.org/abs/2404.16130)



QAs

How effective are the restraint models. from staging how many questions are scrapped/edited




# Reviews
## RedditESS
**Summary:**
The authors create a dataset of social support interactions across PTSD, Depression, Anxiety, Stress, and general mental health forums on Reddit. The authors claim that their dataset is more nuanced for utilising community-based metadata, and that leveraging this dataset enhances LLMs' ability to produce context-sensitive, effective, and supportive responses.

The data is preprocessed, removing posts from bots, spam, adverts, irrelevant posts, and surveys. Of the remaining data, only posts that had been edited, contained comments that had been replied to by the original poster (OP), and where none of the comments were deleted were kept.

The data is labelled in three stages; firstly, the OP's edited initial post and replies to the initial post from the OP are referred to as General Feedback; in the second stage, the comments are classified either positive or negative based on the number of likes received; and the third stage focuses on the OP's responses to individual comments. Stage three uses regular expressions to detect known gratuitous words, and a model from TweetNLP to perform sentiment analysis. The final score for stage three is the product of these.

Subject matter experts reviewed 564 human comments linked to 141 unique posts, representing 13% of the golden dataset. human annotators also ranked comments by their supportiveness on a scale of 1-4. The agreement score, using Fleiss's Kappa is 0.42 which the authors claim reflects moderate agreement.

The authors provide an in-depth analysis of the linguistic differences between the supportive and non-supportive categories. 

The authors align a Llama model by performing supervised fine-tuning and direct preference optimisation using a subset of the golden dataset. The preference of the aligned model outperformed the Llama 2 base model considerably when generating social support.

Two BERT family models are trained to classify supportive and non-supportive comments using 90% of the dataset for training and 10% for evaluation with reported f1 scores of 84% and 85%.

The authors acknowledge that the edited posts can obscure the context. 

**Soundness:**

**Presentation:**
- 3/5 - Figure 1 could be clearer as to what is taking place at each stage of the labelling process, formalising the labelling process would also be useful to the reader.

**Contribution:**
- Curated a novel dataset for social support which takes into account engagement from both the user and community, leveraging social media metadata. 
- Demonstrated the above dataset's effectiveness on classification and generative tasks.

**Strengths:**


**Weaknesses:**
- It would be informative to see some validation of the GPT-4-turbo generated categories. (4.2)
- In taking community/user feedback into account above the opinion of experts, the authors risk positively classifying responses that may be attractive to the OP but ill-advised. (echo-chamber comes to mind...) (3.2.2)
- It is unclear what expertise the 'subject matter experts' have allow them to perform this task. (3.4)
- Comparison between supportive and non-supportive comments seem flawed when taking into account the accuracy of the labelling being very high for positive and very low for negative. (3.4) (para starting line 360)
- Using Landis's 1977 interpretation for Fleiss's Kappa score seems to be misleading since it is not widely agreed upon. Landis's interpretation is based on only 2 classes and 2 annotators where the authors' have 3 annotators and 4 classes. 
**Questions:**
- 
**Rating:**



## Generalizaion through Lexical Abstraction in Transformer Models: The Case of Functional Words - ACL submission
**Summary:**
- 

**Soundness:**

**Presentation:**
- 

**Contribution:**
- 

**Strengths:**


**Weaknesses:**
- 
**Questions:**
- 
**Rating:**




Simon Bowes - embodiment

benchmarks - SNLI RTE for early reasoning benchmarks


What would a paper look like?
- multi agent architectures
- 