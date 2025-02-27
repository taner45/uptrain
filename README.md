<h4 align="center">
  <a href="https://uptrain.ai">
   <img alt="Github banner 006 (1)" src="https://github.com/uptrain-ai/uptrain/assets/108270398/96ac1505-7811-4e12-958e-fce9519542a1"/>
  </a>
</h4>

<p align="center">
<a href="https://demo.uptrain.ai/evals_demo/" rel="nofollow"><strong>Try out Evaluations</strong></a>
-
<a href="https://docs.uptrain.ai/getting-started/introduction" rel="nofollow"><strong>Read Docs</strong></a>
-
<a href="https://join.slack.com/t/uptraincommunity/shared_invite/zt-1yih3aojn-CEoR_gAh6PDSknhFmuaJeg" rel="nofollow"><strong>Slack Community</strong></a>
-
<a href="https://github.com/uptrain-ai/uptrain/issues/new?assignees=&labels=enhancement&template=feature_request.md&title=" rel="nofollow"><strong>Feature Request</strong></a>
</p>

<h4 align="center">
<a href='https://github.com/uptrain-ai/uptrain/blob/main/CONTRIBUTING.md'>
    <img alt='PRs Welcome' src='https://img.shields.io/badge/PRs-welcome-blue.svg?style=shields'/>
  </a>
  <a href="https://github.com/uptrain-ai/uptrain/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/uptrain-ai/uptrain" />
  </a>
  <a href="https://docs.uptrain.ai/getting-started/quickstart">
    <img src="https://img.shields.io/badge/Quickstart-tutorial-orange" alt="Quickstart" />
  </a>
  <a href="https://uptrain.ai/">
    <img src="https://img.shields.io/badge/UpTrain-Website-red" alt="Website" />
  </a>
</h4>

<h4 align="center">
  <img src="https://github.com/uptrain-ai/uptrain/assets/108270398/cf3a3de8-96b6-4fd5-a589-f313cb10bbde" alt="Demo of UpTrain's LLM evaluations with scores for hallucinations, retrieved-context quality, response tonality for a customer support chatbot"/>
</h4>

**[UpTrain](https://uptrain.ai)** is an open-source tool to evaluate LLM applications. UpTrain provides pre-built metrics to check LLM responses on aspects such as correctness, hallucination, toxicity, etc. as well as provides an easy-to-use framework to configure custom checks.

# Pre-built Evaluations We Offer 📝

#### Evaluate the quality of your responses:
1. [Response Completeness](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/response_quality/completeness.ipynb): Grades how if the response completely resolves the given user query.
2. [Response Relevance](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/response_quality/relevance.ipynb): Grades how relevant the generated response is for the given question.
3. [Response Conciseness](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/response_quality/conciseness.ipynb): Grades how concise the generated response is i.e. the extent of additional irrelevant information in the response.
4. [Response Matching](): Operator to compare the llm-generated text with the gold (ideal) response using the defined score metric.
5. [Response Consistency](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/response_quality/consistency.ipynb): Grades how consistent the response is with the question asked as well as with the context provided.

#### Evaluate the quality of retrieved context and response groundedness:
1. [Factual Accuracy](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/context_awareness/factual_accuracy.ipynb): Checks if the facts present in the response can be verified by the retrieved context
2. [Response Completeness wrt Context](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/context_awareness/response_completeness_wrt_context.ipynb): Grades how complete the response was for the question specified with respect to the information present in the context
3. [Context Relevance](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/context_awareness/relevance.ipynb): Evaluates if the retrieved context contain sufficient information to answer the given question

#### Evaluations to safeguard system prompts and avoid LLM mis-use:
1. [Prompt Injection](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/safeguarding/system_prompt_injection.ipynb): Identifys prompt leakage attacks


#### Evaluate the language quality of the response:
1. [Tone Critique](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/language_features/tone_critique.ipynb): Assesses if the tone of machine-generated responses matches with the desired persona.
2. [Language Critique](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/language_features/language_critique.ipynb): Scores machine generated responses on multiple aspects - fluence, politeness, grammar, and coherence.

#### Defining custom evaluations and others:
1. [Guideline Adherence](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/custom/guideline_adherence.ipynb): Grades how well the LLM adheres to a given custom guideline.
2. [Custom Prompt Evaluation](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/custom/writing_custom_evals.ipynb): Evaluate by defining your custom grading prompt.
3. [Cosine Similarity](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/custom/cosine_similarity.ipynb): Calculate cosine similarity between embeddings of two texts.

#### Evaluate the conversation as a whole:
1. [Conversation Satisfaction](https://github.com/uptrain-ai/uptrain/blob/main/examples/checks/conversation/conversation_satisfaction.ipynb): Measures the user’s satisfaction with the conversation with the LLM/AI assistant based on completeness and user’s acceptance.


# Get started 🙌

### Install the package through pip:
```bash
pip install uptrain
```

### How to use UpTrain:

There are two ways to use UpTrain:
1. **Open-source framework:** You can evaluate your responses via the open-source version by providing your OpenAI API key to run evaluations. UpTrain leverages a pipeline comprising GPT-3.5 calls for the same. Note that the evaluation pipeline runs on UpTrain's server but none of the data is logged.

2. **UpTrain API:** You can use UpTrain's managed service to log and evaluate your LLM responses. Just provide your UpTrain API key (no need for OpenAI keys) and UpTrain manages running evaluations for you with real-time dashboards and deep insights.

#### Open-source framework:

Follow the code snippet below to get started with UpTrain.

```python
from uptrain import EvalLLM, Evals
import json

OPENAI_API_KEY = "sk-***************"

data = [{
    'question': 'Which is the most popular global sport?',
    'context': "The popularity of sports can be measured in various ways, including TV viewership, social media presence, number of participants, and economic impact. Football is undoubtedly the world's most popular sport with major events like the FIFA World Cup and sports personalities like Ronaldo and Messi, drawing a followership of more than 4 billion people. Cricket is particularly popular in countries like India, Pakistan, Australia, and England. The ICC Cricket World Cup and Indian Premier League (IPL) have substantial viewership. The NBA has made basketball popular worldwide, especially in countries like the USA, Canada, China, and the Philippines. Major tennis tournaments like Wimbledon, the US Open, French Open, and Australian Open have large global audiences. Players like Roger Federer, Serena Williams, and Rafael Nadal have boosted the sport's popularity. Field Hockey is very popular in countries like India, Netherlands, and Australia. It has a considerable following in many parts of the world.",
    'response': 'Football is the most popular sport with around 4 billion followers worldwide'
}]

eval_llm = EvalLLM(openai_api_key=OPENAI_API_KEY)

results = eval_llm.evaluate(
    data=data,
    checks=[Evals.CONTEXT_RELEVANCE, Evals.FACTUAL_ACCURACY, Evals.RESPONSE_COMPLETENESS]
)

print(json.dumps(results, indent=3))
```
If you have any questions, please join our [Slack community](https://join.slack.com/t/uptraincommunity/shared_invite/zt-1yih3aojn-CEoR_gAh6PDSknhFmuaJeg)


#### UpTrain API:

1. Get your free UpTrain API Key [here](https://uptrain.ai/).

2. Follow the code snippets below to get started with UpTrain.
```python
from uptrain import APIClient, Evals
import json

UPTRAIN_API_KEY = "up-***************" 

data = [{
    'question': 'Which is the most popular global sport?',
    'context': "The popularity of sports can be measured in various ways, including TV viewership, social media presence, number of participants, and economic impact. Football is undoubtedly the world's most popular sport with major events like the FIFA World Cup and sports personalities like Ronaldo and Messi, drawing a followership of more than 4 billion people. Cricket is particularly popular in countries like India, Pakistan, Australia, and England. The ICC Cricket World Cup and Indian Premier League (IPL) have substantial viewership. The NBA has made basketball popular worldwide, especially in countries like the USA, Canada, China, and the Philippines. Major tennis tournaments like Wimbledon, the US Open, French Open, and Australian Open have large global audiences. Players like Roger Federer, Serena Williams, and Rafael Nadal have boosted the sport's popularity. Field Hockey is very popular in countries like India, Netherlands, and Australia. It has a considerable following in many parts of the world.",
    'response': 'Football is the most popular sport with around 4 billion followers worldwide'
}]

client = APIClient(uptrain_api_key=UPTRAIN_API_KEY)

results = client.log_and_evaluate(
    project_name="Sample-Project",
    data=data,
    checks=[Evals.CONTEXT_RELEVANCE, Evals.FACTUAL_ACCURACY, Evals.RESPONSE_COMPLETENESS]
)

print(json.dumps(results, indent=3))
```

To have a customized onboarding, please book a [demo call here](https://calendly.com/uptrain-sourabh/30min).

### Performing experiments with UpTrain:

Experiments help you perform A/B testing with prompts, so you can compare and choose the options most suitable for you. 

```python
from uptrain import APIClient, Evals
import json

UPTRAIN_API_KEY = "up-***************" 

data = [
    {
        "question": "How can you ensure that a designed prompt elicits the desired response from a language model?",
        "context": "nudge the model to generate a desired result. Prompt design can be an efficient\nway to experiment with adapting a language model for a specific use case.",
        "response": "To ensure that a designed prompt elicits the desired response from a language model, you can experiment with different prompt designs that nudge the model towards generating the desired result. This can be an efficient way to adapt the language model for a specific use case.",
        "chunk_size": 200
    },
    {
        "question": "How can you ensure that a designed prompt elicits the desired response from a language model?",
        "context": "Design and save your own prompts\nPrompt design is the process of manually creating prompts that elicit the\ndesired response from a language model. By carefully crafting prompts, you can\nnudge the model to generate a desired result. Prompt design can be an efficient\nway to experiment with adapting a language model for a specific use case.\nYou can create and save your own prompts in Vertex AI Studio. When\ncreating a new prompt, you enter the prompt text, specify the model to use,\nconfigure parameter values, and test the prompt by generating a response. You\ncan iterate on the prompt and its configurations until you get the desired\nresults. When you are done designing the prompt, you can save it in\nVertex AI Studio.\nResponse citations\nIf you are using a text model in Vertex AI Studio like text-bison, you\nreceive text responses based on your input. Our features are intended to produce\noriginal content and not replicate existing content at length. If",
        "response": "To ensure that a designed prompt elicits the desired response from a language model, you can manually create prompts that carefully craft the desired result. By iterating on the prompt and its configurations in Vertex AI Studio, you can experiment and adjust until you achieve the desired results. Additionally, it is important to note that the text models in Vertex AI Studio are designed to produce original content and not replicate existing content at length.",
        "chunk_size": 1000
    }
]

client = APIClient(uptrain_api_key=UPTRAIN_API_KEY)

results = client.evaluate_experiments(
    project_name="Chunk-Size-Experiment",
    data=data,
    checks=[Evals.CONTEXT_RELEVANCE, Evals.RESPONSE_RELEVANCE, Evals.FACTUAL_ACCURACY],
    exp_columns=["chunk_size"]
)

print(json.dumps(results, indent=3))
```

<h4> </h4>

# Key Features 💡


- **[Custom Grading Checks](https://uptrain-ai.github.io/uptrain/operators/language/ModelGradeScore/)** - Write your custom grading prompts to use LLM as an evaluator.
- **[Embeddings Similarity Check](https://uptrain-ai.github.io/uptrain/operators/CosineSimilarity/)** - Compute cosine similarity between prompt-response embeddings
- **[UMAP Visualization and Clustering](https://uptrain-ai.github.io/uptrain/operators/UMAP/)** - Visualize your embedding space using tools like UMAP and t-SNE.
- **[Feature Slicing]()** - Built-in pivoting functionalities for data dice and slice to pinpoint low-performing cohorts.
- **[Realtime Dashboards]()** - Monitor your model's performance in realtime.

# Dimensions of LLM Evaluations 💡

<h4 align="left">
  <img width="600" src="https://github.com/uptrain-ai/uptrain/assets/108270398/6cf080ef-7aec-4609-81e1-25d667401ad4" alt="Different dimensions, metrics or criteria for LLM evaluations"/>
</h4>

We recently wrote about different criteria to evaluate LLM applications and explored grouping them into categories. [Read more about it.](https://uptrain.ai/blog/how-to-evaluate-your-llm-applications)


# Integrations

| Eval Frameworks  | LLM Providers | LLM Packages | Serving frameworks | 
| ------------- | ------------- | ------------- | ------------- | 
| OpenAI Evals ✅ | GPT-3.5-turbo ✅ | Langchain 🔜 | HuggingFace 🔜 |
| EleutherAI LM Eval 🔜 | GPT-4 ✅  | Llama Index 🔜 |  Replicate 🔜 |
| BIG-Bench 🔜 | Claude ✅ | AutoGPT 🔜 |
| | Cohere ✅ | 


# Why UpTrain 🤔?

Large language models are trained over billions of data points and perform really well over a wide variety of tasks. But one thing these models are not good at is being deterministic. Even with the most well-crafted prompts, the model can misbehave for certain inputs, be it hallucinations, wrong output structure, toxic or biased response, irrelevant response, and error modes can be immense. 

To ensure your LLM applications work reliably and correctly, UpTrain makes it easy for developers to evaluate the responses of their applications on multiple criteria. UpTrain's evaluation framework can be used to:

1) **Improve performance by 20%** - You can’t improve what you can’t measure. UpTrain continuously monitors your application's performance on multiple evaluation criterions and alerts you in case of any regressions with automatic root cause analysis.

1) **Iterate 3x faster** - UpTrain enables fast and robust experimentation across multiple prompts, model providers, and custom configurations, by calculating quantitative scores for direct comparison and optimal prompt selection.

1) **Mitigate LLM Hallucinations** - Hallucinations have plagued LLMs since their inception. By quantifying degree of hallucination and quality of retrieved context, UpTrain helps to detect responses with low factual accuracy and prevent them before serving to the end-users.

# What does UpTrain have to offer? 🚀

To make it easy for you to evaluate your LLM applications, UpTrain offers:

1) **Diverse LLM Evaluations** - UpTrain provides a diverse set of pre-built metrics like response relevance, context quality, factual accuracy, language quality, etc. to evaluate your LLM applications upon.

1) **Single-line Integration** - With UpTrain's wide array of pre-built metrics, you can run LLM evaluations in less than two minutes.

1) **Customization** - UpTrain is built with customization at its core, allowing you to configure custom grading prompts and operators with just a python function.

We are constantly working to make UpTrain better. Want a new feature or need any integrations? Feel free to [create an issue](https://github.com/uptrain-ai/uptrain/issues) or [contribute](https://github.com/uptrain-ai/uptrain/blob/main/CONTRIBUTING.md) directly to the repository.

# License 💻

This repo is published under Apache 2.0 license and we are committed to adding more functionalities to the UpTrain open-source repo. Upon popular demand, we have also rolled out a [no-code self-serve console](https://demo.uptrain.ai/dashboard). For customized onboarding, please book a [demo call here](https://calendly.com/uptrain-sourabh/30min).

# Stay Updated ☎️
We are continuously adding tons of features and use cases. Please support us by giving the project a star ⭐!

# Provide feedback (Harsher the better 😉) 

We are building UpTrain in public. Help us improve by giving your feedback **[here](https://docs.google.com/forms/d/e/1FAIpQLSezGUkkC0JoEvx-0gCrRSmGutA-jqyb7kl2lomXv302_C3MnQ/viewform?usp=sf_link)**.

# Contributors 🖥️

We welcome contributions to UpTrain. Please see our [contribution guide](https://github.com/uptrain-ai/uptrain/blob/main/CONTRIBUTING.md) for details.

<a href="https://github.com/uptrain-ai/uptrain/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=uptrain-ai/uptrain" />
</a>
