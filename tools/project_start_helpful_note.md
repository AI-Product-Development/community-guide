## These are specific to the stockmarket API video by Dave 

These may or may not apply for other projects. Please use your judgement.

### Pre-requisites:
- Create project folder in VSCode
- Create docs folder within projects folder
- Create prompts folder within projects folder and copy the prompt files
- Open copilot CTRL+ALT+i and make sure you are using <b>Edit</b> mode (not Read)
- Drag the prompts files into Copilot
- in VSCode terminal : <uv init> followed by <uv add SQLModel>

### Steps to create artefacts

- PRD document creation prompt:
<code>In the docs folder I want you to create a PRD document for an API that provides stock market um data the stock market
data.  This stock market data for this API is going to be mock data. Use O2_product_manager as your guide</code>
Make sure to review the created doc (in the docs folder (you are running the AI not the other way around)
- SA document creation prompt:
<code>Using 03_solution_architect please create a file /docs/SA.md this is a backend application so we don't need anything
from the front end.</code>
Make sure to review the created doc (in the docs folder (you are running the AI not the other way around)
- DA document creation prompt:
<code>Okay great. Now create using 04_data_architect.md a document /docs/DA.md which outlines the data architecture.</code>
Make sure to review the created doc (in the docs folder (you are running the AI not the other way around)

### General fixes (To be structured into a suitable place later)

- To display Mermaid diagrams in .md (markdown) files such as data architecture install extension "Markdown Preview Mermaid Support" in VScode (CTRL+SHIFT+X for windows env and then search for it)
- uv add SQlite
- uv add prisma
