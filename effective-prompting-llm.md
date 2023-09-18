# Prompting Guide 

## Table of Contents

- [Introduction](#introduction)
- [Techniques](#techniques)
- [Models and Risks](#risks)
- [License](#license)
---

<h1 id=introduction align="center"> Introduction</h1>

<details>
  <summary>
    What is Prompt Engineering?
  </summary>
    Prompt engineering is a relatively new discipline for developing and optimizing prompts to efficiently use language models (LMs). Prompt crafting isn't just about constructing clever queries; it helps improve the capacity of LLMs on a wide range of common and complex tasks. It's the art of forging a relationship with these linguistic giants, where understanding their capabilities and limitations is just the beginning.
    
</details>

---

<h1 id=techniques align="center">Techniques</h1>




**Zero-Shot prompting:** Zero-shot prompting is a method in artificial intelligence where a language model is given a task or question without any specific training examples. Instead, it uses its pre-existing knowledge and the provided instructions to generate a response or perform the task. It's a way to make AI models more versatile and adaptable to different tasks without extensive training.

>Zero-shot prompting is like asking a very smart friend a question without giving them any background information or examples. They rely on their general knowledge and the way you phrase the question to give you an answer. It's a way for AI to answer questions or do tasks it hasn't been specifically trained for. For example, you might ask, "What are the main ingredients in pizza?" and the AI can answer without having seen a pizza recipe before.


**Few-Shot Prompting:** 

Few-shot prompting is a technique used with large-language models to improve their performance on complex tasks. While these models can do well without any prior examples (zero-shot), they struggle with more complicated tasks. Few-shot prompting involves giving the model a few examples (demonstrations) in the prompt to help it learn and generate better responses. This method becomes effective when the models are sufficiently large.

> For example, imagine we want the model to use a new word in a sentence, like "whatpu" or "farduddle." By providing a single example sentence using these words in the prompt, the model learns how to use them correctly. This process is called "1-shot" prompting. If the task is harder, we can try with more examples (e.g., 3-shot, 5-shot, 10-shot) to further improve the model's performance.

Prompt:
```
A "whatpu" is a small, furry animal native to Tanzania. An example of a sentence that uses
the word whatpu is:
We were traveling in Africa and we saw these very cute whatpus.
To do a "farduddle" means to jump up and down really fast. An example of a sentence that uses
the word farduddle is:
```
Output:
```
When we won the game, we all started to farduddle in celebration.
```
---
**Chain-of-Thought Prompting**

Chain-of-thought (CoT) prompting, introduced in Wei et al. (2022), allows for complex reasoning by breaking tasks into intermediate steps. When combined with few-shot prompting, it improves results on intricate tasks requiring reasoning.

![COT](img/cot.PNG)

> In the provided example, the prompt presents groups of numbers and apples. By demonstrating the reasoning process in the answer (A), the model effectively solves the task. It involves breaking down complex reasoning tasks into a series of intermediate steps or thought processes. This helps the model understand and reason through the problem step by step. It's important to note that this capability emerges in large language models, as stated by the authors.

---
ChatGPT answers the question with purely Chain of Thought

![COT](img/chat.PNG)
---


<h1 id=risks align="center">Models and Risks</h1>



| Model                   | Release Date | Size (B) | Checkpoints                        | Description                                                      |
|-------------------------|--------------|----------|-----------------------------------|------------------------------------------------------------------|
| Falcon LLM              | May 2023     | 7, 40    | [Falcon-7B](https://huggingface.co/tiiuae), [Falcon-40B](https://huggingface.co/tiiuae)  | Falcon LLM is a foundational large language model (LLM) with 40 billion parameters trained on one trillion tokens. TII has now released Falcon LLM – a 40B model. |
| PaLM 2                  | May 2023     | -        | -                                 | A Language Model that has better multilingual and reasoning capabilities and is more compute-efficient than its predecessor PaLM. |
| Med-PaLM 2              | May 2023     | -        | -                                 | Towards Expert-Level Medical Question Answering with Large Language Models |
| Gorilla                 | May 2023     | 7        | [Gorilla](https://github.com/ShishirPatil/gorilla)                  | Gorilla: Large Language Model Connected with Massive APIs |
| RedPajama-INCITE        | May 2023     | 3, 7     | [RedPajama-INCITE](https://huggingface.co/togethercomputer)         | A family of models including base, instruction-tuned & chat models. |
| LIMA                    | May 2023     | 65       | -                                 | A 65B parameter LLaMa language model fine-tuned with the standard supervised loss on only 1,000 carefully curated prompts and responses, without any reinforcement learning or human preference modeling. |
| Replit Code             | May 2023     | 3        | [Replit Code](https://huggingface.co/replit)              | replit-code-v1-3b model is a 2.7B LLM trained on 20 languages from the Stack Dedup v1.2 dataset. |
| h2oGPT                  | May 2023     | 12       | [h2oGPT](https://github.com/h2oai/h2ogpt)                   | h2oGPT is a large language model (LLM) fine-tuning framework and chatbot UI with document(s) question-answer capabilities. |

[link1]: #your_link_here
[link2]: #your_link_here
[link3]: #your_link_here
[link4]: #your_link_here
[link5]: #your_link_here
[link6]: #your_link_here

---

## Risks

This section emphasizes the importance of considering the potential dangers and misuses of language models (LLMs), especially when applied in real-world applications. It discusses risks related to prompt injections and harmful behaviors. Additionally, it mentions the need to address issues such as generalizability, calibration, biases (including social biases), and factuality when working with LLMs.


### Factuality

When utilizing Language Models (LLMs), it's common for them to generate responses that appear coherent but can sometimes be entirely fictitious. Improving their accuracy and dependability hinges on the effective optimization of prompts. Here, we discuss some technical strategies to address this issue:

### Ground Truth Integration

One way to bolster the reliability of LLM-generated responses is to incorporate verified information, such as excerpts from pertinent articles or Wikipedia entries, into the contextual information provided. This practice significantly diminishes the chances of the model generating fabricated or inaccurate responses.


Generate a response that incorporates verified information, such as an excerpt from a relevant article or Wikipedia entry.

#### Response

> What are the symptoms of COVID-19?

> The most common symptoms of COVID-19 are fever, cough, shortness of breath, and fatigue. Other symptoms may include muscle aches, headache, sore throat, congestion or runny nose, nausea or vomiting, and diarrhea.

According to the Centers for Disease Control and Prevention (CDC), the following are the most common symptoms of COVID-19:

- Fever or chills
- Cough
- Shortness of breath or difficulty breathing
- Fatigue
- Muscle aches
- Headache
- Sore throat
- Congestion or runny nose
- Nausea or vomiting
- Diarrhea
- Loss of taste or smell

#### Explanation

This response incorporates verified information by including an excerpt from the CDC website. This excerpt provides a comprehensive list of the most common symptoms of COVID-19, and it is also a credible source of information.

> Ground truth integration is an important technique for improving the reliability of NLP models. By incorporating verified information into responses, NLP models can reduce the risk of fabricating information and provide more accurate and informative responses.


### Response Calibration

Response calibration involves fine-tuning the LLM by adjusting its parameters to minimize response variability. Furthermore, you can instruct the model to explicitly acknowledge uncertainty by generating responses like "I don't know" when it lacks a precise answer. This enhances the model's ability to provide accurate and meaningful information.

### Mixed Prompt Approach

By designing prompts that consist of a combination of questions and potential answers, encompassing both within and beyond the model's knowledge domain, you help the LLM better discern the boundaries of its expertise. This mixed prompt approach contributes to more contextually appropriate and factual responses.



---

<h1 id=license align="center"> License</h1>
This project is licensed under the MIT License

---
Copyright (c) 2023 Interact-Brands
---

