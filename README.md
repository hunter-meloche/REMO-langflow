# REMO-langflow
GPT-4 and the [REMO memory system](https://github.com/daveshap/REMO_Framework) are combined to create a highly intelligent chatbot with a long-term memory. This provides an easy way to interface with it using [LangFlow](https://github.com/logspace-ai/langflow).

This is not a complete or ideal implementation. Feel free to improve upon it or use it to better understand the tech it uses.

## How to use
- Launch REMO
- Launch langflow and import the json from this repo
- Put in your OpenAI key in the ChatOpenAI node on the left
- Chat... It will save the information you give it (add_message), but you need to tell it to "organize memories" (maintain_tree) to put those new memories in the place where the retrieval function (search) can find them. Ideally this would be automatically triggered, but for the purposes of testing, I've not done this.


![image](https://user-images.githubusercontent.com/123516285/232245663-7951c991-c9ed-4115-a9d3-021a0682eb40.png)

## Implemented
- Saving memories
- Finding memories
- Organizing memories (must be called for new memories to be retrievable)
