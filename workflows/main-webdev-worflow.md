## web dev workflow

I will try to get asn idea of the architecture of a project first by

1. get tech stack and basic architecture

- asking chat gpt to design a project like what i would want. then i ask it lots of questions about why it chose the technology/ frameworks it did and what alternatives there are. 
- then i get it to summarise the project, and paste it into another chatbot and ask it to review the choices. I do this for heaps of stuff.

2. Ask an agent to build the project with this tech stack and create concise and easy to ready docs for it. 

manus ai - builds and tests full stack app. I think genspark does this too. 
replit - i'm not sure if this does full stack as well . 
v0 - just for UI. 

Now i have the starting framework for my project. 

3 - create docs. 



 functional specs -- basically I just write a big file detailing everything I  want the app to do in my own words. maybe i get gemin2.5 or chatgpt to rewrite it, but i check it very thoroughly to make sure it has understood what i want. 

technical specs - a document explaining the overall architecture that would have been likely created in step 2.
 
 I use cursor agent, copilot, ai studio, or whatever to create mermaid diagrams of data flow of different parts of the app so i can visualise it as well. 

 the idea is to get the whole project summarise in a few files which you can copy into any chatbot you want to ask a question about. 

4 add features
- using gemini coder and aistudio i then past the whole project into the ai studio context and say something like 

"Let's implement this feature (describe the feature i want to add in detail or even better get chatgpt to write a detailed description of the feature from my description and add it to its own file under functional specs folder).  read the docs and carefully implement this feature abiding by all SOLID principles"

then i paste the generated code back into vscode and run it. if it works great. if it doesnt:

debug process 
try to avoid doing debugging directly in ai-studio chat. rather create sandboxes by asking the cursor agent to do the debugging. 
1. try the quick fix. 
paste the error in cursor agent and ask 
"give me an analysis of this error (explain all the info about what caused i)" i usually paste the debug-prompt.md into the chat as well.
if it thinks it can fix it
"implement this fix"


Modularity use SOLID principles - i don ltknow fully what this means 