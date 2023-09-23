# llama-cpp-langchain-chat
Lightweight Llama.cpp chatbot made with langchain and chainlit. This project mainly serves as a simple example of langchain chatbot and is a template for further langchain projects. Uses chainlit as a dropin UI chatbot so there is basically no ui code. 

### Prompt Support
Supports alpaca text prompts, v2 and tavern style json and yaml files and V2 and tavern png cards. Text prompts need to start with the instruct portion, but the response is appended to the text prompt template. Avatar images need to be in the same folder as the prompt file. V2 and Tavern png files get a copy of the image without exif data in the project temp file.

### Card Format
'name' : 'char_name'<br>
The name for the ai character. When using json or yaml, this is expected to correspond to avatar image. name.png or name.jpg.<br>
'description' : 'char_persona'<br>
The description for the character personality. Likes, dislikes, personality traits.<br>
'scenario' : 'world_scenario'<br>
Description of the scenario. This roughly corresponds to things like "You are a hr customer service having a discussion with a customer. Always be polite". etc.<br>
'mes_example' : 'example_dialogue'<br>
Example dialogue. The AI will pick answer patterns based on this<br>
'first_mes' : 'char_greeting'<br>
A landing page for the chat. This will not be included in the prompt.

See https://zoltanai.github.io/character-editor/ for a character card editor.

### Configs
See the configuration params in .env.example file

### Running the chatbot
You might want to build with cuda support. You need to pass FORCE_CMAKE=1 and CMAKE_ARGS="-DLLAMA_CUBLAS=on" to env variables
>pipenv install - requirements.txt<BR>
pipenv shell<BR>
(optional for cuda support)$env:FORCE_CMAKE=1<BR>
(optional for cuda support)$env:CMAKE_ARGS="-DLLAMA_CUBLAS=on"<BR>
(optional for cuda support)pip install llama-cpp-python==0.2.6 --force-reinstall --upgrade --no-cache-dir --no-deps<BR>
cd src\llama_cpp_langchain_chat<BR>
chainlit run chat.py<BR>

OR<BR>
>hatch env create<BR>
hatch shell<BR>
(optional for cuda support)$env:FORCE_CMAKE=1<BR>
(optional for cuda support)$env:CMAKE_ARGS="-DLLAMA_CUBLAS=on"<BR>
(optional for cuda support)pip install llama-cpp-python==0.2.6 <BR>--force-reinstall --upgrade --no-cache-dir --no-deps<BR>
cd src\llama_cpp_langchain_chat<BR>
chainlit run chat.py<BR>

The chatbot should open in your browser<BR>

![chatbot](/readme_pics/chatbot.png)