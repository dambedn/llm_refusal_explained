# AI Reflection: Midpoint (Phase I)

AI-aided pair:
- First Name Last Name, Student ID: Elouie Rain Galan, k12450898
- First Name Last Name, Student ID: Jasmin Felber, k11807837

## Reflection
Working with an LLM as an interactive support created an environment where we can have an exchange of ideas, particularly the LLM takes a rough idea and is able to refine it for execution. This led to an overall faster deployment of ideas into code and deeper analysis. We initially worked individually and used the LLMs as a consulting tool to help in brainstorming ideas for ways to explore how the model behaves and afterwards, we met as a pair to discuss our results. 

The LLM helped in creating clear and differentiable contexts used for testing responses of the Gemma 3 model and was useful in refining the word choice for the names of the contexts to be used in visualization. For analysis, we initially created simple statistics of the responses made by the model across different contexts and the group decided to explore the idea of transforming the input prompts into embeddings using a sentece transformer, which will be downprojected into 2D space using UMAP. 

LLM assistance was used for refining the UMAP plots in terms of how it can be more easily understood by an audience. Since plotting safe and unsafe responses in one plot made it more difficult to understand the visualization, so we evaluated the use of having 2 subplots that showed either only safe or only unsafe plots as suggested by the LLM. This 2 subplot approach made the visualization less cluttered and more easily interpretable due to less information overload.

Although LLMs can provide assistance in brainstorming, these would also give some suggestions for plots that can be considered repetitions of previous plots or added too much complexity to the presentation of data. For example, we already had barplots which summarized the results of the responses of the Gemma 3 model, but the LLM would continue to suggest more bar plots that describes the same information, or more complex plots that would take some time to explain to an audience. As such, we decided to reject these redundant suggestions and only kept more relevant visualizations such as the UMAP projections. 
