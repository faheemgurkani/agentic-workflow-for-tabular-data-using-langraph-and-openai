# Agentic AI Workflow for Tabular Data using LangGraph & OpenAI

## Project Overview

This project showcases an **Agentic AI System** leveraging the power of **LangGraph**, **OpenAI's LLMs**, and **LangChain Tools** to perform intelligent workflows on tabular datasets stored in a DuckDB database. The system demonstrates how autonomous AI agents can interact with structured data, execute tools, and maintain stateful, iterative reasoning.

## Pipeline Architecture

The system follows these core stages:

### 1. Environment & Dependency Setup

* **Tools**: `requirements.txt`
* **Functionality**:

  * Installs all necessary Python packages, including LangChain, LangGraph, OpenAI SDK, and database utilities.

### 2. Data Configuration

* **Tools**: `os`, `duckdb`
* **Functionality**:

  * Defines dataset location (`../data/choc_ai_dataset`) and relevant table names (e.g., `menu`, `order`, `order_item`).
  * Uses DuckDB as the SQL-based storage for querying tabular data.

### 3. Schema & Data Validation

* **Tools**: `pydantic`
* **Functionality**:

  * Establishes structured data models for tool responses.
  * Ensures robust, type-validated communication between tools and AI agents.

### 4. Tool Development (LangChain Tools)

* **Tools**: `@tool` decorator from `langchain_core.tools`
* **Functionality**:

  * Implements modular tools for specific database tasks:

    * Fetching menu items.
    * Retrieving order information.
    * Summarizing order item details.
  * Each tool returns structured, validated outputs.

### 5. LLM Integration

* **Tools**: `ChatOpenAI`, `langchain_core.messages`
* **Functionality**:

  * Utilizes OpenAI's conversational models for reasoning and decision-making.
  * Structures agent communication using message types like `AIMessage`, `HumanMessage`, and `SystemMessage`.

### 6. Agentic Workflow with LangGraph

* **Tools**: `StateGraph`, `ToolNode`, `MemorySaver`
* **Functionality**:

  * Builds an agentic, stateful workflow using LangGraph's `StateGraph`.
  * Registers tools as nodes in the graph.
  * Defines workflow transitions, checkpoints, and message flow.
  * Employs `MemorySaver` to persist conversational state.

### 7. Execution & Visualization

* **Tools**: `IPython.display`
* **Functionality**:

  * Demonstrates AI-agent driven interactions with the tabular dataset.
  * Displays results and workflow visualizations within the notebook.

## Technology Stack

| Category           | Tools/Packages                                        |
| ------------------ | ----------------------------------------------------- |
| Database & Queries | `duckdb`                                              |
| LLM Integration    | `langchain_openai`, `ChatOpenAI`                      |
| Agentic Workflow   | `langgraph` (`StateGraph`, `ToolNode`, `MemorySaver`) |
| Messaging System   | `langchain_core.messages` (`AIMessage`, etc.)         |
| Data Validation    | `pydantic`                                            |
| Visualization      | `IPython.display`                                     |
| Utility            | `os`, `json`, `typing_extensions`                     |

## Setup Instructions

1. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

2. **Prepare Dataset**

   * Place your tabular data files (e.g., `.csv`) in the `../data/choc_ai_dataset` directory.
   * Ensure tables like `menu`, `order`, and `order_item` are present or modify table references accordingly.

3. **Environment Variables**

   * Add your OpenAI API key as needed, e.g.,

     ```bash
     export OPENAI_API_KEY=your_openai_key_here
     ```

## Example Usage

```python
# Example of running the Agentic AI workflow
graph = StateGraph()
graph.add_tool_nodes(...)
graph.add_llm_nodes(...)
graph.add_transitions(...)
graph.compile()
graph.run("Show me all orders with desserts")
```

## Conclusion

This notebook demonstrates how modern agentic AI frameworks, coupled with LLMs and LangChain's modular tooling, can create autonomous, intelligent workflows for interacting with structured tabular data sources.

Ideal for:

* AI-driven data analysis
* Conversational querying of databases
* Prototyping autonomous reasoning systems over enterprise data
