# REMO-langflow
GPT-4 and the [REMO memory system](https://github.com/daveshap/REMO_Framework) are combined to create a highly intelligent chatbot with a long-term memory. This provides an easy way to interface with it using [LangFlow](https://github.com/logspace-ai/langflow).

This is not a complete or ideal implementation. Feel free to improve upon it or use it to better understand the tech it uses.

![image](https://user-images.githubusercontent.com/123516285/232272096-23763e8a-9f44-446a-80c9-ea4a696bb0b5.png)

## Setup
- Launch REMO
- Launch langflow and import the json from this repo
- Put in your OpenAI key in the ChatOpenAI node on the left
- Chat...

## How it works
It will automatically save new information you give it with an `add_message` API call. Missing information will be automatically searched for as well (`search`). If the relevant information cannot be found, `rebuild_tree` is automatically called to integrate newer memories into retrievable summaries. You can manually tell it to "organize memories" (`maintain_tree`) to create summaries from message pairs and the same can be done for `rebuild_tree` by saying "rebuild tree". 

If `maintain_tree` or `rebuild_tree` is called before at least 2 messages have been saved, you'll get a benign error:
```
The 'n_clusters' parameter of KMeans must be an int in the range [1, inf). Got 0 instead.
```
The reason why this is happens is because the L2 message pairing system takes a new message and connects it to the last message as a pair. Tree maintainence creates summaries based on L2 pair data. So if you have 2 pieces of information that are in separate pairs, you won't be able to get both with one call to search the memory. This is where rebuilding the tree comes in to mesh all of the related data together into comprehensive summaries.

## Implemented
- Saving memories
- Finding memories
- Organizing memories (must be called for new memories to be retrievable)
- Rebuilding memory tree (Useful to trigger when it returns incomplete or incorrect information)

## Known issues
- sometimes hallucinates information when creating inferences based upon input data
- does not always use REMO tools when appropriate
