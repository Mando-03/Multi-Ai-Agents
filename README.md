# Multi Ai Agents For Products Analysis

## Overview

This notebook implements Multi Ai Agents using Crewai to assist that helps our comapny Rankyx to find and evaluate suitable products for it using our agents. The system uses a multi-agent approach to perform the entire procurement process from search query generation to final report creation.

## Key Features

1. **Multi-Agent System**: Implements 4 specialized AI agents working sequentially:
   - Search Query Recommendation Agent
   - Search Engine Agent
   - Web Scraping Agent
   - Procurement Report Author Agent

2. **End-to-End Procurement Process**:
   - Generates targeted search queries
   - Performs web searches
   - Extracts product details from e-commerce sites
   - Creates a professional procurement report

3. **Integration with Multiple APIs**:
   - Tavily API for search
   - ScrapeGraph API for web scraping
   - Gemini 2.0 Flash LLM for agent reasoning
   - AgentOps for monitoring

## Notebook Structure

1. **Setup & Installation**
   - Installs required packages (tavily-python, scrapegraph-py, crewai)
   - Configures API keys from Google Colab secrets
   - Sets up output directory

2. **Agent Definitions**
   - Each agent is defined with specific roles, goals, and tools
   - Tasks are created with detailed descriptions and expected outputs
   - Pydantic models ensure structured data output

3. **Tool Implementations**
   - Search engine tool using Tavily
   - Web scraping tool using ScrapeGraph

4. **Crew Execution**
   - Agents are organized into a sequential crew
   - Kickoff with specific parameters for coffee machine procurement in Egypt

## How It Works

1. **Search Query Generation**:
   - Creates targeted e-commerce search queries with specific brands/types
   - Formats queries with website domains (e.g., "DeLonghi coffee machine :www.amazon.eg")

2. **Web Search**:
   - Executes searches using generated queries
   - Filters results by confidence score and e-commerce validity

3. **Product Extraction**:
   - Scrapes product pages for key details (price, specs, images)
   - Evaluates and ranks products based on value

4. **Report Generation**:
   - Creates a professional HTML report with:
     - Executive summary
     - Methodology
     - Product comparisons
     - Recommendations

## Output Files

The process generates 4 output files:
1. `step_1_suggested_search_queries.json` - Generated search queries
2. `step_2_search_results.json` - Raw search results
3. `step_3_search_results.json` - Extracted product details
4. `step_4_procurement_report.html` - Final procurement report

## Usage Example

```python
crew_results = rankyx_crew.kickoff(
    inputs={
        "product_name": "coffee machine for the office",
        "websites_list": ["www.amazon.eg", "www.jumia.com.eg", "www.noon.com/egypt-en"],
        "country_name": "Egypt",
        "no_keywords": 10,
        "language": "English",
        "score_th": 0.10,
        "top_recommendations_no": 3
    }
)
```

## Requirements

- Python 3.x
- API keys for:
  - Gemini
  - Tavily
  - ScrapeGraph
  - AgentOps (optional)

## Installation

```bash
pip install -qU tavily-python scrapegraph-py
pip install -qU crewai[tools,agentops]
```
