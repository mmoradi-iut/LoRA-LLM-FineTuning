# LoRA-LLM-FineTuning
LoRA-based fine-tuning of LLMs for automated test case generation
<br>
<img width="800" src="https://github.com/mmoradi-iut/LoRA-LLM-FineTuning/blob/main/image.png">

In this repository, you can find information, results, data, and source codes of the empirical study devoted to evaluation of LoRA-based fine-tuning of LLMs in the context of automated test case generation. The method and experiments are described and discussed in the paper titled "An empirical study of LoRA-based fine-tuning of large language models for automated test case generation".

<h2>Models under study</h2>
<p>Open-source models:</p>

<p>•	<b>DeepSeek</b></p>
<p>•	<b>Llama</b></p>
<p>•	<b>Mistral</b></p>

<p>Proprietary models:</p>

<p>•	<b>GPT-4.1</b></p>
<p>•	<b>GPT-4.1-mini</b></p>
<p>•	<b>GPT-4.1-nano</b></p>

<h2>Dataset</h2>
<p>The dataset was collected from an industrial software testing environment, consisting of real-world software requirements and their corresponding manually authored test cases. Each data instance links a requirement artifact to one associated test case, ensuring strong traceability between inputs and outputs. The requirements and test cases originate from a test management system and cover a wide range of functional scenarios, including UI behavior, API interactions, integration logic, and configuration management.</p>
<p>The dataset is divided into a training set and a test set. The training set contains 2,583 instances, while the test set consists of 288 instances. Each instance includes a requirement name and description paired with a corresponding test case name, test case type, test case description, and test steps. The requirements are predominantly written in natural language and often include acceptance criteria, numbered conditions, and domain-specific terminology. The test cases reflect practical testing practices and vary in complexity, ranging from short validation checks to long, multi-step procedural tests.</p>

<p>The input to the model consists of:</p>

<p>•	<b>Requirement name</b>: a concise textual identifier describing the feature or change request.</p>
<p>•	<b>Requirement description</b>: a detailed natural language specification, often including acceptance criteria, functional constraints, and expected system behavior.</p>

<p>Given these inputs, the model is expected to generate the following outputs:</p>

<p>•	<b>Test case name</b>: a concise and descriptive title summarizing the intent of the test.</p>
<p>•	<b>Test case type</b>: a classification of the test (e.g., functional UI, functional API, regression, usability).</p>
<p>•	<b>Test case description</b>: a high-level explanation of the test objective and scope.</p>
<p>•	<b>Test steps</b>: a structured, ordered list of executable test steps, typically including actions and expected results.</p>

In order to get permision and have access to the datasets, send an email to m.moradi-vastegani@tricentis.com.

<h2>Experimental pipeline</h2>
<p>This study follows a structured and end-to-end research, development, and experimentation pipeline designed to systematically evaluate LLMs for automated test case generation. The overall pipeline consists of seven main stages: (1) data processing and preparation, where raw requirement–test case pairs are cleaned and transformed into a consistent training format; (2) model selection, covering both open-source and proprietary LLMs; (3) prompt design and engineering, in which a unified instruction-based prompt and output schema are defined; (4) fine-tuning configuration, including the setup of parameter-efficient fine-tuning mechanisms such as LoRA; (5) model fine-tuning, where models are adapted to the downstream task using the prepared dataset; (6) evaluation configuration, including the design of automated evaluation prompts and scoring criteria; and (7) execution of evaluation experiments to assess and compare model performance. This modular pipeline allows individual components to be adjusted or extended while maintaining experimental consistency and reproducibility.</p>

In order to get permision and have access to the source codes of the experimental pipeline, send an email to m.moradi-vastegani@tricentis.com.

<h2>Tuned LoRA parameters</h2>
<p>The effectiveness of LoRA depends strongly on the choice of hyperparameters that govern the capacity and behavior of the low-rank adaptation. In this study, we systematically explored several key LoRA parameters to identify configurations that yield optimal performance for automated test case generation.</p>

<p>•	<b>LoRA rank (r)</b>:  It determines the dimensionality of the low-rank matrices and directly controls the expressive capacity of the adaptation. Higher ranks allow the model to learn more complex task-specific transformations but increase the number of trainable parameters and computational overhead. Lower ranks improve efficiency but may limit adaptation capability.</p>
<p>•	<b>LoRA alpha or scaling factor (α)</b>: It controls the magnitude of the LoRA update relative to the frozen base weights. The scaling factor effectively rescales the learned low rank matrices during training and inference, influencing training stability and convergence behavior. Proper tuning of this parameter is important to ensure that the adaptation neither overwhelms the base model nor becomes too weak to capture task-specific patterns.</p>
<p>•	<b>LoRA dropout</b>: It applies dropout to the low-rank adaptation during training to improve generalization and reduce overfitting, particularly when training data is limited. Dropout introduces stochastic regularization, encouraging the model to rely on robust patterns rather than memorizing specific training examples.</p>

<h2>Evaluation criteria</h2>
<p>To enable scalable and consistent evaluation across multiple models and configurations, we adopted a LLM-based evaluation approach, using GPT-4o as an automated judge. GPT-4o was selected due to its strong reasoning ability, instruction-following performance, and demonstrated effectiveness in comparative evaluation tasks involving structured outputs. In this framework, GPT-4o receives the requirement, the model-generated test case, and the corresponding human authored reference test case, and produces structured evaluation scores across predefined criteria. </p>
<p>The evaluation framework assesses generated test cases using nine complementary criteria, designed to capture multiple dimensions of quality relevant to software testing. These criteria extend beyond simple textual similarity and focus on semantic correctness, completeness, clarity, and practical usability. These are nine evaluation criteria in this study:</p>

<p>•	<b>Semantic similarity</b>: It evaluates how closely the overall meaning and intent of the generated test case align with the reference test case, emphasizing conceptual alignment rather than lexical overlap.</p>
<p>•	<b>Information coverage</b>: It measures how comprehensively the generated output captures important details such as preconditions, actions, expected outcomes, and edge cases.</p>
<p>•	<b>Critical content match</b>: It assesses whether essential elements such as roles, system components, data attributes, or UI elements are correctly preserved.</p>
<p>•	<b>Structural and format accuracy</b>: It evaluates whether the output follows the expected structure, including a clear title, type classification, and logically ordered test steps.</p>
<p>•	<b>Omission</b>: It measures the extent to which important information is missing, with higher scores indicating minimal missing content.</p>
<p>•	<b>Hallucination</b>: It assesses whether the generated test case introduces unsupported or irrelevant information not grounded in the requirement or reference.</p>
<p>•	<b>Ambiguity</b>: It evaluates the clarity and precision of the language used, focusing on whether the test case can be easily understood and executed.</p>
<p>•	<b>Redundancy</b>: It measures the degree of unnecessary repetition, with higher scores indicating concise and well-organized outputs.</p>
<p>•	<b>Diversity and novelty</b>: It captures whether the generated test case introduces valid alternative interpretations or improvements beyond the reference while remaining logically sound.</p>
