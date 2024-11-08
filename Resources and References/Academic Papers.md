
## Large Language Models (LLMs)

## Embeddings
- [T-FREE: Tokenizer-Free Generative LLMs via Sparse Representations for Memory-Efficient Embeddings](https://www.semanticscholar.org/reader/efc8e68d9a0d002141c49cf0101678880621132c)
	- Trigram tokenisation addresses large and growing vocab size of models upwards of 250k+ tokens

## Benchmarking
- [An Examination of the Robustness of Reference-Free Image Captioning Evaluation Metrics](https://aclanthology.org/2024.findings-eacl.14/)
	- 
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

## Architectures


## Knowledge Retrieval
- [From Local to Global: A Graph RAG Approach to Query-Focused Summarization](https://arxiv.org/abs/2404.16130)



QAs

How effective are the restraint models. from staging how many questions are scrapped/edited