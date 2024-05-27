## Efficient Text to SQL
Source: https://medium.com/dataherald/high-accuracy-text-to-sql-with-langchain-840742133b83

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
