## Dynamic LLM-Powered Agent Network for Task-Oriented Agent Collaboration (DyLAN)
[Original paper](https://arxiv.org/abs/2310.02170)

### Main Contributions
1) **Static agent teams:** Prior frameworks ([[CAMEL]], [[AgentVerse]]) use a fixed set of agents throughout the task. Potentially unhelpful agents still participate and clutter the process
2) **Fixed communication structures:** Even when agents interact in multiple rounds, the communication flow stays constant. DyLAN introduces a **temporal feed-forward network (T-FFN)** that allows the structure to evolve during the task, pruning or rerouting interactions based on performance.
3) **No principled team optimisation:** Earlier methods either handcraft teams using human priors or generate agents based on fixed prompts. DyLAN introduces an **unsupervised, principled selection mechanism** (Agent importance Score) to form an optimised team based on actual contributions during a trial run.
4) **Inefficient inference:** Redundant or poor-performing agents inflate API usage. DyLAN's **early stopping** and **agent pruning** make inference more efficient without sacrificing performance.

### Dynamic Team Composition
1) **Task-specific specialisation:** Dynamic composition ensures that only agents with relevant 'expertise' contribute, improving accuracy and relevance.
2) **Efficiency:** In simpler tasks, dynamic selection avoids unnecessary computation. 
3) **Noise and interference:** Redundant or unhelpful agents can introduce conflicting or low-quality messages - hurting the quality of final outputs. Removing them mid-collaboration leads to clearer, more focused reasoning.

### Temporal Feed-Forward Networks (T-FFNs)
T-FFNs are used in DyLAN to model **multi-round, multi-agent collaboration** over time. They abstract agent interactions like a computational graph:
- 