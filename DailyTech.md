### Efficient Text to SQL
Source: [Medium](https://medium.com/dataherald/high-accuracy-text-to-sql-with-langchain-840742133b83)

<b>KEYWORDS</b> </br>
Using `Dataherald API Wrapper` in `langchain` library
</br>
This api also delivers the result in matplotlib library

Notable Plotting tool
```python
# A function to plot a list
def plot_and_save_array(dict_of_values):
  dict_of_values = json.loads(dict_of_values.strip().replace("'", '"'))
  items = list(dict_of_values.keys())
  values = list(dict_of_values.values())
  plt.figure(figsize=(5, 3))
  plt.plot(items, values, marker='o')
  plt.title("Array Plot")
  plt.xlabel("Items")
  plt.ylabel("Values")
  plt.xticks(rotation=45)
  plt.grid(True)
  identifier = uuid.uuid4().hex[:6] + ".png"
  plt.savefig(identifier)
  plt.show()
  return "success"

plotting_tool = StructuredTool.from_function(
    func=plot_and_save_array,
    name="Plotting Results",
    description="A tool which receives a valid json object with keys being the x axes values and for each key we should have a single value",
)
```
***

### LLM App Levels
Source: [Youtube/ Neural Hacks](https://youtu.be/UIV_odcp-aw?si=cu905hfrsAYh7HEs)
</br>

*Top to Base (Most Complex to Least Complex)*
1. LLM OS
    - LLM which can control the os
    - Chars
      - Yes - In Context Memory, Externcal Knowledge, Tools & Peripheral Tools.
2. Agent
    - LLM which can do a given task autonomously is an agent.
    - It can acess to math, g_search, doc loader tools etc 
    - Chars
      - Yes - In Context Memory (Remember), External Knowledge & Tools
      - No -  Peripheral Tools
3. RAG
    - Chatbot or QA System with an external data source(pdf, webpages etc) for knowledge
    - Chars
      - Yes - In Context Memory (Remember) & External Knowledge
      - No - Tools & Peripheral Tools
4. Chat Bot
    - Having a sequence of conversation with LLMs
    - Just Raw ChatGPT Interactions
    - Chars
      - Yes - In Context Memory (Remember)
      - No - External Knowledge, Tools & Peripheral Tools
5. General QA
    - Answering questions based on self-knowledge or given a context
    - Just for intent extraction, complete sentence activity.
    - Chars
      - No - In Context Memory, External Knowledge, Tools, Peripheral Tools





