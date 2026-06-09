# EVE Platform Tour

In this folder we find the material for **"Building Agentic Earth Intelligence: A Hands-On Tour of the EVE Platform and Tool Ecosystem"**.

The main resource is `Agentic_EVE.ipynb`. Through it we explore how to move from a plain LLM workflow to a fully agentic Earth Observation workflow, wrapping real geospatial APIs as tools, exposing them via MCP, and driving them through EVE's agentic reasoning loop.

## What You Learn

- How to explore EVE's REST API (document retrieval, RAG generation, hallucination detection)
- What distinguishes a reasoning LLM from a full agent, and how the ReAct loop works in practice
- How to design tool functions an LLM can reliably call (Nominatim geocoding example)
- How MCP standardizes tool discovery and invocation (FastMCP server over HTTP)
- How to navigate EVE's Tool Registry and contribute new MCP servers
- How to invoke EVE's agentic endpoint and read tool-call execution traces

## Resources

- `Agentic_EVE.ipynb`: end-to-end tutorial notebook
- `Agentic_EVE_presentation.pdf`: slide deck accompanying this session

## Folder Contents

```
.
├── Agentic_EVE.ipynb               # hands-on tutorial
├── Agentic_EVE_presentation.pdf    # session slide deck
├── images/                         # figures used in the notebook
└── .env                            # local credentials (not committed)
```

## Prerequisites

- Python 3.10+
- Jupyter environment (JupyterLab, VS Code notebooks, or similar)
- An EVE platform account for the login-based sections (see Early Access below)

## Environment Setup

### Access Colab
Colab is a free platform that can be used to easily run python notebooks, we suggest to run the notebook into Colab to have a easy and smooth experience:

1. Open the Colab app [here](https://colab.research.google.com/):
2. Login/Signup 
<img src="./images/colab_login.png", style="max-width: 700px">
3. Download the notebook from github

To run the notebook uploa

Create a local `.env` file (same directory as the notebook) with the provided credential:

```env
BASE_URL=https://<your-eve-platform-base-url>
EMAIL=<your-account-email>
PASSWORD=<your-account-password>
```

> Keep credentials private. Do not commit `.env` files.

The notebook uses these packages (install once with the commented `%pip` cell):

- `python-dotenv`
- `httpx`
- `geopy`
- `requests`
- `fastmcp`

## Run the Notebook

1. Open `Agentic_EVE.ipynb`.
2. Run the **Setup** cells first (dependency install + `.env` loading).
3. Execute sections in order:
  - **EVE platform tour**: REST API walk-through (retrieve, RAG, hallucination detection)
  - **From LLMs to Agents**: core concepts, ReAct loop
    - **Part I**: From services to tools (Nominatim geocode/reverse-geocode)
    - **Part II**: Model Context Protocol: build and serve an MCP server with FastMCP
    - **Part III**: EVE's Tool Registry: discover, authenticate, and call community MCP servers
    - **Part IV**: Agentic EVE: invoke the LangGraph-based agent and inspect traces
4. Review the trace visualisations to understand model-to-tool orchestration.

## Troubleshooting

- **Missing dependencies**: re-run the install cell and restart the kernel if needed.
- **Auth errors**: verify `BASE_URL`, `EMAIL`, `PASSWORD` in `.env`.
- **No tool results**: confirm login/token generation succeeded before registry/agentic calls.
- **Kernel state issues**: restart the kernel and run all cells from the top in order.

## EVE Platform & Early Access

EVE is an open, agentic platform for Earth Observation and Earth Sciences, funded and supported by **ESA Φ-lab**.

- **Public launch**: Q3 2026. [Register to be notified](https://eve.philab.esa.int/launch) on the official ESA Φ-lab page.
- **Open source today**: models, data, and pipelines are freely available at [huggingface.co/eve-esa](https://huggingface.co/eve-esa). The tool layer is open source at [github.com/eve-esa/mcp-tool-registry](https://github.com/eve-esa/mcp-tool-registry).
- **Early access / contribute**: to get a preview of the hosted deployment or contribute to the project before the public launch, reach out to us directly:
  - [antonio.lopez@picampus-school.com](mailto:antonio.lopez@picampus-school.com)
  - [jino.rohit@picampus-school.com](mailto:jino.rohit@picampus-school.com)
  - [alex.atrio@picampus-school.com](mailto:alex.atrio@picampus-school.com)

## Funding

This project is supported by the European Space Agency (ESA) Φ-lab through the Large Language Model for Earth Observation and Earth Science project, as part of the Foresight Element within FutureEO Block 4 programme.

## Citation

If you use this project in academic or research settings, please cite:

```bibtex
@misc{atrio2026evedomainspecificllmframework,
      title={{EVE}: A Domain-Specific {LLM} Framework for Earth Intelligence}, 
      author={Àlex R. Atrio and Antonio Lopez and Jino Rohit and Yassine El Ouahidi and Marcello Politi and Vijayasri Iyer and Umar Jamil and Sébastien Bratières and Nicolas Longépé},
      year={2026},
      eprint={2604.13071},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2604.13071}, 
}
```

