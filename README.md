# A hands-on guide to LLM-based AI Agents
#### ML Prague 2025
#### Philipp Wendland <pwendland@deloitte.de>
This notebook contains exercises for the workshop at ML Prague 2025. The goal is to implement an AI Agent that can assist you in exploring a new city and planning various trips according to your preferences.
***
###### Sources: 
- https://huggingface.co/blog/smolagents
- https://huggingface.co/docs/smolagents/index
- https://github.com/anthropics/anthropic-cookbook/
- https://platform.openai.com/docs/overview
***

The notebook consists of 4 exercises, starting with a simple prompt and ending in creating a multi-agent system using smolagents.

##### Overview over exercises

## Exercise 1: Simple Prompt
This exercise will ensure your environment, API keys and accesses are configured correctly. Additionally you will create a simple prompt to use as a reference point when building your agent.

Complete the following items:
- [ ] Set up API key
- [ ] Adjust the prompt to your preferences
- [ ] Examine the simple output from the LLM


## Exercise 2: Prompt Workflow
Create a prompt workflow (aka prompt-chain) to break down the task of planning an itinerary into multiple steps. The `sequential_chain` method always passes the output of the previous generation between steps. In the first step `add_information` is passed.

Complete the following items:
- [ ] Edit the list of prompts `create_itinerary_prompts`, add at least one more sequential prompt. Compare the output to the results from Exercise 1
- [ ] Write the `additive_chain` function, where all previous generated output is passed between steps, change the prompt-list if necessary and re-run the chain
- [ ] **BONUS**: Try a different use case: e.g., create a marketing pitch for the sight-seeing tour and translate it to a different language / tonality.

## Exercise 3a: Tool Calling
Before introducing the smolagents framework, we will implement a tool call using standard OpenAI functionalities. We will add the option for tool calls into the prompt-chain.

- [ ] Examine the implemented tool call for obtaining current weather information.
    - [ ] Extend both `llm_call_openai` and `sequential_chain` to be able to handle tool calls
    - [ ] Add the tool call in the beginning of the prompt chain to add current weather information to the planning.


## Exercise 3b: Tool Calling with smolagents
Create your first "agent" using smolagents.

- [ ] Examine the simple way to setup a CodeAgent in smolagents
- [ ] Add the implemented get_weather tool and the DuckDuckGoSearchTool to a Code Agent and let it create an intinerary as before. Run the agent several times and adjust the prompt for the best results. Notice potential issues with setting up an agent like this.


## Exercise 4: Multi-agent systems
As you saw in the last exercise, giving one agent a longer list of tools usually does not yield the best results. It is best practice to use agents to solve specific tasks (e.g., one agent to perform web-search and another agent to obtain weather information). In this exercise we will create a multi-agent system
- [ ] Examine the multi-agent system consisting of two `ToolCallingAgents` and one manager agent (a `CodeAgent`)
- [ ] Add an additional agent to the multi-agent system. First, implement an a new tool of your choice (e.g., image generation to create a postcard , tourist summary of famous sights, connect to the GoogleMaps API to plan routes between sights) 


***

## Further Reading
- https://github.com/huggingface/smolagents/blob/main/src/smolagents/vision_web_browser.py