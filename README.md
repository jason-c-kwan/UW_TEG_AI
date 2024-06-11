# Tiny Earth Genomics AI Assistant

If you would like to try out the Tiny Earth Genomics AI assistant I made, you can access it on [Hugging Chat](https://hf.co/chat/assistant/666773d008ce33273d7057e1). I am still in the process of optimizing it over the summer so it might not be the best right now but will probably improve.

You can view the prompt I am using for the assistant [here](prompts/TEG_bot_prompt.md).

The assistant has access to the following files:

1. [The course handbook](knowledge_files/handbook/Handbook_SP2024.docx.md)
2. [The course syllabus for Spring 2024](knowledge_files/syllabus/PHMSCI_254_syllabus_SP2024.docx.md)
3. Rubrics for some assignments in the course: a [poster](knowledge_files/poster_rubric/Poster_rubric.md), a [mini-report](knowledge_files/mini_report_rubric/Mini_report_rubric.md) and the [final report](knowledge_files/final_report_rubric/Final_report_rubric.md).

Note: These files are currently a bit of a mess. I will try to clean them up soon.

Users should be able to ask the assistant about any of the material in the course, and how to do all the exercises featured in the syllabus/handbook. Another major application is troubleshooting errors that arise during class. 

## Building your own AI assistant

### LLM Providers

First thing you have to do is figure out what platform you want to use, as they all have advantages and disadvantages. However, also note that this area is extremely fast-moving, so in addition to what I write here it will always be worth doing your own research. I have also only written here about the platforms I have experience with. While there are many websites that you can chat with LLMs for free, there are fewer which allow you to use your own prompts and knowledge files.

[ChatGPT](https://chat.openai.com) from OpenAI has a really good free model (GPT-4o), but you need to be a subscriber ($20/month) in order to create your own GPTs (what OpenAI call custom AI assistants). I have also found that while the GPT-4o model is very good, it is not quite as intelligent as GPT-4, which can only be accessed by subscribers. In our testing GPT-4-based assistants are really good at following instructions and understanding the knowledge files, but GPT-4o did a lot worse (with the same prompt). Carefully re-wording the prompt might overcome this.

[Poe](https://poe.com) from Quora has a free tier where you get 3000 credits per day (subscribing for $20/month gets you 1,000,000 per month). The good thing about Poe is that one subscription allows you to use all sorts of different LLMs and compare them to each other. Each LLM costs a different amount in terms of credits per message. You can make custom AI assistants, called "Bots", but there is a limited selection of LLMs you can use and some are only available to subscribers. We found this a bit limiting. For example, if you make a bot based on GPT-4o (shown as ChatGPT in Poe), at 300 credits per message, students can only send ten messages a day to the assistant.

[Hugging Chat](https://huggingface.co/chat/) from Hugging Face is a free platform which has a lot of the features of other platforms, but with open source LLMs. This is the platform I am currently using because it allows both the free creation of AI assistants and free and unrestricted use of them by students. The current iteration of the assistant uses the [llama3-70b-instruct](https://huggingface.co/meta-llama/Meta-Llama-3-70B-Instruct) model developed by Meta, which is probably the current state of the art for open source models. One downside of this model is its context window (i.e. conversation memory) is only 8,000 tokens (about 6,000 words). With long troubleshooting conversations, this could be a problem, although Meta have said they will release longer context models soon.

### Writing a prompt

If you have a look at the [prompt](prompts/TEG_bot_prompt.md) I am using, you will see that there are three main parts. You can use this as a starting point to adapt your own prompt. 

**Base context**. This section describes the assistant's role and the types of user it will be interacting with (i.e. the audience). 

**Custom knowledge**. This section describes the different custom knowledge documents that the assistant has access to, a summary of what information is in them, and instructions on when to refer to the different files.

**Instruction**. This section contains specific instructions on how the assistant should act in different circumstances, such as different types of questions. You could, for example, tell the assistant to not always give answers straight away but rather ask questions designed to get the student to figure out the next logical step. Another example is in my prompt, I tell the assistant to refuse to answer questions which are irrelevant to the TE class. I also attempt to stop the assistant from doing students' assignments for them.

In writing your prompts make sure that you are specific about what you want. However, one thing to note is that a major differentiator between LLMs is how well they follow instructions. So in optimizing an assistant, you will want to both improve the prompt and also try other models since if you have one that is not good at following instructions it will be difficult to improve the prompt much.

### Setting up the AI assistant

Note: I have included here instructions on how to do this on [Hugging Chat](https://huggingface.co/chat/) because it is not quite as self explanatory as with [ChatGPT](https://chat.openai.com). In ChatGPT you can go to the [GPTs](https://chatgpt.com/gpts) page and click "+Create", and then follow the instructions. 

In the Hugging Chat interface, you cannot upload knowledge files. Instead you must point it to publicly accessible links. An easy way to do this is to have your documents in a Github repository (Github is the website you are on right now). They must either be in html or plain text format. To make a repository on Github:

1. Register a username on [Github](https://github.com) and log in.
2. Click the green "New" button to make a new repository. You will have to pick a name for it and follow the instructions. Note: For the files to be accessible to the assistant, the repository must be set to "Public" rather than "Private".
3. Once you are in your repository, click the grey "Add file" button and then either "Create new file" (if you want to type or paste in the text into the Github website) or "Upload files" if you want to directly upload the files.

