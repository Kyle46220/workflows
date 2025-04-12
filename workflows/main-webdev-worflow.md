## web dev workflow

I will try to get asn idea of the architecture of a project first by

## 1. get tech stack and basic architecture

- asking chat gpt to design a project like what i would want. then i ask it lots of questions about why it chose the technology/ frameworks it did and what alternatives there are. 
- then i get it to summarise the project, and paste it into another chatbot and ask it to review the choices. I do this for heaps of stuff.

## 2. Ask an agent to build the project with this tech stack and create concise and easy to ready docs for it. 

manus ai - builds and tests full stack app. I think genspark does this too. 
replit - i'm not sure if this does full stack as well . 
v0 - just for UI. 

Now i have the starting framework for my project. 

## 3 - create docs and understand project architecture.

 functional specs - basically I just write a big file detailing everything I  want the app to do in my own words. maybe i get gemini 2.5 or chatgpt to rewrite it, but i check it very thoroughly to make sure it has understood what i want. this is a more detailed version of what I asked for in step 2 but being way more specific and using more of the jargon. 

architecture specs - a document explaining the overall architecture that would have been likely created in step 2. 

technical patterns - i don't always understand these, but i ask chat gpt to write a technical patterns document for the project based on the functional specs and architecture. this defines best practise and keeps thing consistent. this can also be implemetned with cursor rules (SEE cursor-set-up.md)

glossary.md - to define all the terms used ini the project. 

 I also use cursor agent or whatever to create mermaid diagrams of data flow of different parts of the app so I can visualise it as well. 

 the idea is to get the whole project summarised in a few files which you can copy into any chatbot you want to ask a question about. 

## 4. add features

- using gemini coder and aistudio i then paste the whole project including all the docs and specs into the ai studio context and say something like 

"Let's implement this feature (describe the feature i want to add in detail or even better get chatgpt to write a detailed description of the feature from my description and add it to its own file under functional specs folder).  read the specs folder, other docs, and cursor rules and carefully draft an implementation plan for this feature, abiding by all SOLID principles, and project patterns"
then i review the plan discuss and make change with ai if needed, adn if its for a big refactor i chagen i will save it to a file. 
then i ask the ai 
"read implementation plan. do step 1 of the plan carefully."
"read implementation plan. do step 2 of the plan carefully." etc. get it to check the plan between every step. 

then i paste the generated code back into vscode/cursor whatever and run it. if it works great (write change summary see below). if it doesnt:

## 5. debug process 
I try to avoid doing debugging directly in ai-studio chat so the ai doesn't have too many things to worry about in the one chat. rather I create sandboxes by asking the cursor agent to do the debugging. 

1. try the quick fix. 
paste the error in cursor agent and ask 
"give me an analysis of this error (explain all the info about what caused i)" i usually paste the debug-prompt.md into the chat as well.
if it thinks it can fix it
"implement this fix"
if the fix works, rollback/revert the changes in the cursor agent.  get the agent to summarise the fix and then paste it back into the main ai studio chat, and get this agent to re-implement the fix. SEE UPDATE DOCS SECTION. 

2 if the quick fix doesn't work, I stop debugging in cursor because it will make a mess, get it to write a detailed error report I save to "non-spec docs" folder in my project. and i make sure to revert/undo the changes cursor agent made. i will give the error report to ai studio in one of 2 ways.
 theres a few options from now
 - option 1 - go back and adjust the ai studio prompt. go back to step 4 and rewrite the prompt. if the ai is making something that's not what i want, i might try to describe it better in the prompt, and add the error report I just generated to the prompt as well. 

 - option 2 - do an in depth debug with ai studio in the existing chat. paste the error report and ask ai studio to come up with a plan for debugging this error, and then get it to implement the plan. ask it to request information from you (eg error logs or screenshots)and go back and forth with ai studio untili it figures it out. usually it will do it eventaully. try to give it more context if it struggles (error logs, screenshots, user reports). its smart enough to figure out most bugs but only if it has enough information. when it works move on to UPDATE DOCS

this step is very important. its like saving your work. 

## 6. UPDATE DOCS after you've fixed the bug get ai studio to also write a "change summary" based on the template and save this in the same folder as the functional specs documents you have. 
do this every time you get a feature working or do a refactor. the change summaries build up to make a really solid set of docs that the agent can use to understand the project. then every time I ask to plan a new feature i make sure it reads the docs first. then it won't create shit that breaks shit as much.

also get it to update the glossary.md file you created if it thinks its necessary. 

At this point I can also ask it to create a cursor rule to prevent the bug from happening again. See cursor set up file


the main development loop is 
I decribe what i want > the ai creates a precise document > the ai creates a plan > the ai implements > i describe the error > the ai creates a precise document etc. 

 

other ideas

Modularity -  use SOLID principles - I don't know fully what this means but i always ask it to do it and it helps. it stops everything from breaking when one thingi changes. 

code reviews and refactors. i will often get one chat bot to review the work of another and then take suggestions. and every so often i will get ai stuidio to review the whole codebase by SOLID principles. 