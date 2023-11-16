---
layout: post
title:  "Can Gen AI really do data analysis?"
date:   2023-11-16 10:08:26 +0100
categories: GenAI-technology
---


Generative AI offers the possibility of analyzing and visualizing data by describing what you want to do in natural language, without the need for coding, manipulation of spreadsheets, or specialist tools.  Not only would such a capability make analysis much faster within an organization, but it would enable a much wider set of people within an organization, without training in technical analytics tools, to conduct analysis. Data Analysts and Data Scientists Beware!

However, hype is one thing and reality another. Some articles I have read seem astounded that Gen AI can identify that there are missing values and calculate an average. For me, that’s not really analysis. What’s more, there are already tools on the market that do that for you without writing a line of code. What I really want to know is whether Gen AI can execute more complex analyses.

### **Testing Gen AI’s Data Analysis Capability**

Not convinced by the hype, I decided to test whether I could execute the kind of analyses a graduate economist or data analyst might be asked to do; namely, calculate growth rates, plot trends, and generate a forecast.

Specifically, I created an assistant via the Open AI API and asked it to do the following, using GDP per Capita data from the World Development Indicators dataset (freely available [here](https://databank.worldbank.org/source/world-development-indicators)):

1. "Analyse the data for Switzerland and the UK”
2. "Calculate annual average growth in GDP per capita for the UK and Switzerland for each decade from 1900 to 2020”
3. “Plot a chart of GDP per Capita over time for Switzerland and the UK”
4. “Forecast GDP per Capita growth rates for the next five years”
5. “Plot charts showing the trends used to generate the forecast”

The code, results, and data I used for this experiment can be found on [GitHub](https://github.com/LUNDR/LLM_experiments/tree/main/data_analysis) (although the whole experiment could be executed via the [OpenAI Playground UI](https://platform.openai.com/playground) without the need for any code)

### **Key findings**

- **The ability of the Gen AI-powered assistant to execute the instructions and reason through errors or difficulties is impressive.** For example, it overcame the fact that was only data from 1990 rather than 1900. It also (on most runs) selected the most appropriate approach to calculate average growth rates (CAGR, rather than a simple average of annual rates). It also produced the charts required with little difficulty. Gen AI clearly has the potential to remove a lot of the heavy lifting (i.e. fiddling with code) involved in data analysis, however, data analysts and data scientists should not worry about their jobs just yet.

**Chart of GDP per Capita overime produced by my Generative-AI powered assistant**

![Title](/impromptu/assets/ch_uk_gdp_per_capita.png)


- **Rubbish in, Rubbish out. Poorly formatted and labeled input data are a problem.** The spreadsheet file containing the data to be analyzed contained metadata in the first few rows. Given that the Gen AI always selects the Pandas package in Python to do the analysis, this generates an error when trying to read the data, on a few runs the Assistant was able to work through the error and amend how it was reading in data. However, this used a lot of tokens and several times I breached token limits. A couple of times the Assistant requested further information about the data. In the end, I included instructions to skip the first few rows in the initial prompt.

- **Gen AI models are unimaginative and require hand-holding when deciding which analyses to perform.** My first prompt, which was deliberately vague was mostly greeted with a request from the assistant for more specific instructions about what to analyze. A couple of times a basic description of the data was given. Similarly, when asked to forecast, it mostly did a basic linear projection of GDP per Capita and then calculated growth rates from the slope of the line. Not completely crazy, but not really particularly meaningful. Human intervention is needed to guide the analysis.

- **You don’t always get the same result.** The nature of Generative AI models is such that you are not guaranteed the same result every time you submit the same prompt. Often variation is small, but it can be important and lead to the need for more tokens to allow for a longer reasoning chain. Open AI is working on greater consistency, however, at present it remains a risk for organizations wanting to include Gen AI in data analysis pipelines.

- **On some runs the Gen-AI powered assistant made small, but important mistakes.** For example, on at least one run I made, it omitted the Purchasing Power Parity (PPP) designation in the titles of the charts produced; describing the data as ‘GDP per Capita at current $ ‘ rather than’..at current $ PPP”, which in terms of the meaning and interpretation of the data is important.

- **It cost me around $0.5 to run the experiment end-to-end using GPT-4 Turbo.** Doing multiple runs, being indecisive about what I wanted to see, and testing out bits of code meant I spent around $7 on this experiment. If you are creating thousands of graphs and analyses then clearly costs are going to mount quickly, however compared to the cost of a Data Analyst’s time this is fairly cheap. It’s clear that Generative AI has huge potential to increase the productivity of Data Analysts, Data Scientists and Economists alike.

### **The Future of Data Analysis with Generative AI**

Generative AI has huge potential to augment the work that Data Analysts do and its capabilities will only get better. It can eliminate hours spent looking through documentation to find exactly the right code to produce the required analysis or chart. However (for the time being at least), a human analyst is required to determine the questions to ask in order to extract interesting and relevant insight, to ensure data are read correctly and errors are avoided.

Applications developed on top of Generative AI in the Data Analytics field will seek to provide ‘under the hood’ prompts that limit the variability of responses, provide standardized formatting and error checking along with directing the model toward a particular type of analysis in a particular situation. All of this will enhance the speed of organizations in executing analysis, however, this will not eliminate the need for expert human analysts, and may conversely increase their demand as more people within an organization seek to access analysis.

### **A Note on Assistants and Agents**

To undertake analysis I needed to make use of what is called an ‘Agent’. The reason for this is that a large language model alone will only produce the results of calculations in so far as that particular calculation is contained in the texts on which it was trained. It will not execute calculations or draw charts in its vanilla form: When I asked ChatGPT to “Calculate the average GDP per Capita for each decade from 1900 to 2020 for Switzerland and the UK” I replied that it didn’t do such calculations and was given instructions on how to do the calculation in a spreadsheet.

This is where agents come in. Agents have access to ‘Tools’ that enable them to execute specific actions, such as undertake a web search or execute a block of code. They use LLMs as a way of reasoning through a task. So when you ask an agent to make a calculation the LLM will return the instructions or block of code appropriate to the request described in the prompt, it will execute the code and then if there are errors returned it will extend the prompt and re-execute until it believes the task to be accomplished or a token limit is reached.