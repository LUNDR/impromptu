---
layout: post
title:  "What are Large Language Models (LLM) for and how do they work?"
date:   2023-09-10 10:08:26 +0100
categories: GenAI-technology
---

#### **What are Large Language Models?**

Large Language Models (LLMs) have become all the rage, thanks primarily to Open AI’s providing public access to ChatGPT in November 2022. ChatGPT ignited huge interest given its ability to provide coherent and human-sounding responses to a broad range of instructions and questions, typed in natural language. Since the release of ChatGPT, a number of other organisations have offered public access to their LLMs, including Google (PaLM), Anthropic (Claude), Technology Innovation Institute (Falcon), and Meta (LLama). For a longer list of available LLMs see here.

These models have billions of parameters are are trained on petabytes of data. When given an input question or instruction they predict the most appropriate string of words in response. Beyond their ability to write jokes, compose poems, and instantly resolve the most indignant of dinner table debates, LLMs have demonstrated capabilities that could transform many business operations and things we do as individuals in our everyday lives. The potential uses of LLMs include:

- High-quality chatbots, able to answer a broad range of questions and remember and respond to previous user inputs, without the need to provide exhaustive lists of model questions and responses.

- The ability to create entire essays, blog posts, or emails based on a short description of the desired subject and style.

- Summarization of texts, from either publicly available or privately held sources, with the ability to choose the structure, style, and focus of the summary.

- Generation of code to create software using natural language instructions.

- Answering questions that require factual recall or logical reasoning.

- Analysis of data and creation of visualisations using only Natural Language instructions.

- Extraction of key information and sentiment from texts without needing a large database of examples to train on.

- Ideation. Generation or expansion of ideas to help design and develop marketing materials, film scripts or new products. 

Large Language Models do not do all of these activities perfectly, out of the box. New models are being released regularly improving on previous ones or specialised for particular domains. At the same time, there is a scramble to explore and build applications on top of LLMs which enable users to leverage the power of these models for particular use-cases without altering the model itself. This means programmatically adapting user input through providing additional instructions to the LLM (prompt engineering — more on that later), enriching LLM responses with access to up-to-date domain-specific information (e.g. holiday prices), or enabling LLMs to slot seamlessly into particular workflows.

#### **How do LLMs work?**
When you pass an LLM text it predicts what the most appropriate next tokens (portions of words) should be, given the input text. The billions of parameters used to make a prediction reflect the patterns in language that the model has ‘learned’ through the training process in which it was exposed to petabytes of text, from books, webpages, and other documents. As such LLMs don’t really understand the meaning of any input text in the way a human does. However, their ability to generate appropriate responses given the context is very impressive. On the flip side, LLMs are also capable of giving authoritative and coherent-sounding answers that are completely wrong. This is known as hallucination and is a significant problem that has to be accounted for when implementing an LLM into a live use case.

#### **Are LLMs really going to have a big impact on our lives?**
It’s early days for LLMs, and we’re definitely in the upswing of the hype cycle. Expectations that LLMs will either make us all redundant or the release of chatGPT marked the beginning of the end of humanity are overdone. However, emerging research suggests that impacts on productivity in some domains will be significant: A study of 5000 customer support agents found that a Generative AI assistant improved the number of issues resolved per hour by 14% (Brynjolfsson, Li, Raymond, 2023), while a study of GitHub’s copilot functionality, found that software developers using it completed tasks 56% quicker (Peng et al, 2023).

As with any technology with the potential to improve our lives, there will also be people seeking to put them to more nefarious uses, such as impersonation of living people, cheating on exams, generation of disinformation, fraud, and enabling cyber attacks. People will fall victim to the malign uses of LLMs. We will also see governance and policing of the use of LLMs becoming an increasingly visible part of public debate.