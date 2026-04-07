# LoRA-LLM-FineTuning
LoRA-based fine-tuning of LLMs for automated test case generation

In this repository, you can find information, results, data, and source codes of the empirical study devoted to evaluation of LoRA-based fine-tuning of LLMs in the context of automated test case generation. The method and experiments are described and discussed in the paper titled "An empirical study of LoRA-based fine-tuning of large language models for automated test case generation".

<h2>Models under study</h2>
<p>Open-source models:</p>

<p>•	DeepSeek</p>
<p>•	Llama</p>
<p>•	Mistral</p>

<p>Proprietary models:</p>

<p>•	GPT-4.1</p>
<p>•	GPT-4.1-mini</p>
<p>•	GPT-4.1-nano</p>

<h2>Dataset</h2>
<p>The dataset was collected from an industrial software testing environment, consisting of real-world software requirements and their corresponding manually authored test cases. Each data instance links a requirement artifact to one associated test case, ensuring strong traceability between inputs and outputs. The requirements and test cases originate from a test management system and cover a wide range of functional scenarios, including UI behavior, API interactions, integration logic, and configuration management.</p>
<p>The dataset is divided into a training set and a test set. The training set contains 2,583 instances, while the test set consists of 288 instances. Each instance includes a requirement name and description paired with a corresponding test case name, test case type, test case description, and test steps. The requirements are predominantly written in natural language and often include acceptance criteria, numbered conditions, and domain-specific terminology. The test cases reflect practical testing practices and vary in complexity, ranging from short validation checks to long, multi-step procedural tests.</p>

In order to have access to the datasets and source codes, and get permisions, send an email to m.moradi-vastegani@tricentis.com.
