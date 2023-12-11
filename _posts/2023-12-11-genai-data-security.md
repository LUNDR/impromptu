---
layout: post
title:  "Gen AI & data security: risks you should consider"
date:   2023-12-11 10:08:26 +0100
categories: GenAI-technology
---
f you are planning to use or build applications powered by Generative AI it's worth taking a moment to think about data security. By that, I mean considering whether you are confident that your data or your users’ data will not end up being used or exposed to third parties who shouldn’t be seeing it. Failure to protect confidential data can result in personal embarrassment,  brand damage, loss of IP, and, depending on the case, a hefty fine from the regulator.

Data security is not a new concern, but the nature of Generative AI creates some distinct risks and challenges. How seriously you need to take these risks depends on the status of the data you want to pass through any Generative AI model and on your appetite for risk: If you are just using publicly available data then you may not need to worry about what’s happening to your data. However, if your data is commercially sensitive or contains personal details about individuals (Personally Identifiable Information - PII), then you need to take these risks seriously.

**Data security risks around Gen AI you should be thinking about**

The most common way of working with Generative AI models is via API calls to a model provider: A user inputs a question or request in the form of a prompt into a web-based interface (such as ChatGPT), which may include different types of data as part of the context. The content of that prompt is sent over the internet to a third-party model provider (such as Open AI).  That third party passes the data to the model and a result is sent back, over the internet, to the application where the user inputs the data. 

From a data security point of view, the biggest concern with this way of using Generative AI models is that once data has been inputted into the interface (or the API request is sent) it leaves your control. Once out of your control data could fall into the wrong hands or be seen by someone who shouldn’t be seeing it. Particular concerns with Generative AI include:

1. **Confidential data being used by a third-party provider to retrain models. Your** data may be used in the training of a Generative AI model, another user could get access to your confidential data through clever or accidental prompt engineering. Up to March 2023, OpenAI explicitly stated that it was using data provided to it via interactions with ChatGPT to retrain models. OpenAI (and other providers) have now changed their policy and explicitly state that they do not use your data for training, but you should always check terms and conditions.

2. **Even if not used to train any model, your data may be accessible to other users through clever, or accidental prompting.** While there’s no reason not to believe that providers act in good faith when they say they are not using your data for training, you need to trust the quality of any provider's processes for protecting data. Leakage of data into model training or model outputs could happen: a bug in the code, or an oversight in the architecture such as the capture of logs to track errors, or a failure to fully isolate the previous prompts of other users - because for example, answers to common prompts are cached -  are all possible. 

3. **Applications built on-top of LLMs may, under-the-hood, be sending data on multiple users as part of the context in a prompt to the model**. This data may be easy to extract.  While the application may be built with the intention that users do not have access to this data, it may be possible for users to obtain others’ data via prompts inputted to the application, despite the best intentions of the application designers. While model providers and application builders continue to develop safeguards against these sorts of risks, the capabilities of models and prompts are still being discovered. 

4. **Third Party Providers of LLMs store your data for a period of time.** OpenAI stores your data for at least 30 days. Other providers have similar policies. This is a risk because it can be accessed by others, legitimately or otherwise. Open AI states that for its Enterprise version access to that data is restricted to “Authorized OpenAI employees will only ever access your data for the purposes of resolving incidents, recovering end user conversations with your explicit permission, or where required by applicable law.” However, that it will not fall into the wrong hands in error is a matter of trust. The fact is that you cannot audit a third-party provider, you simply have to trust them.

5. **Data is captured while crossing the internet to the third party provider.** There are more or less secure ways of passing data over the internet. It is possible for someone, with the right software, to capture the data you enter into a web-page. That said, this will probably not be the biggest source of concern for most organisations using Gen AI models. Today the use of  encryption of data in transit via the use of HTTPS (rather than HTTP) connections is widespread and major foundation model providers all provide an HTTPS connection. More of a concern should be third party applications which sit between any user and the model provider, which are not properly secure. 

**A more secure route to working with Gen AI models?**

Some data privacy risks can be mitigated by working with Gen AI models through existing cloud providers. Rather than users sending data directly to Open AI, models can be accessed via a cloud provider such as Microsoft Azure (Azure Open AI ML) or Google Cloud.

In this setup, models are hosted by the cloud provider. Contextual data, prompts, and data for fine-tuning can be stored and managed within an individual organisation's cloud estate. The data itself and much of the processing can be kept inside a so-called “virtual private cloud (VPC)”, allowing strong control and visibility over who or what can access your data. In addition, encryption of the data can also be managed directly by the organisation using Gen AI with customer-managed keys for encrypting the data. 

Typically, you pay more per query under this model, and you pay for other resources used to manage the data. In return, you are getting a lot more governance and control around data being provided to models. 

However, it is important to understand that data is still passed to the third-party organisation (Azure/GCP) hosting the foundation model. Models do not sit inside your VPC. What’s more most providers keep your data for at least 30 days and may undertake checks to ensure models aren’t being used for nefarious purposes. Again whether this is the right way of working, comes down to a question of trust: do you trust Google or Microsoft enough to keep your data secure?

For maximum control over your data’s security, you can host your own models. This is not possible with Open AI’s models as they are not open source. However if you wish to use LLAMA (from Meta) or PaLM (from Google) you can host the models yourself and keep them entirely isolated from the public internet if needed. This hasn’t so far emerged as a popular way of working because:

- You can’t make use of best-in-class models from providers who do not open source (i.e. Open AI).

- You need a lot of compute: while for some use cases, smaller or quantized models may suffice, models with a performance comparable to GPT-3.5/4, with an acceptable number of tokens per minute will require a lot of GPU RAM (we’re talking hundreds of GB). If you are renting from a cloud provider that’s likely to mean tens of thousands of dollars a month. Buying your own GPU to host on-premise could also set you back hundreds of thousands of dollars (and you will probably have to wait for them given the demand for GPUs at present).

- You will need to invest resources and expertise to set up and manage the model and applications built on top of it. 

While more secure, this way of working means slower development time and a much higher upfront cost. For some organisations, that have a large number of users and strong regulatory or internal requirements for data security this may make sense; but it will not be for all.