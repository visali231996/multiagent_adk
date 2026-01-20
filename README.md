# AI Recipe, Shopping & Wallet Manager (Google ADK + MCP)

A multi-agent AI system built using Google ADK, LiteLLM, and MCP (Model Context Protocol) that helps users:

Find recipes from a DOCX-based JSON database

Filter recipes by ingredients, cuisine, time, and diet

Fetch live market prices for ingredients

Calculate total cost

Manage a virtual wallet and approve purchases

This project demonstrates agent orchestration, tool calling, live web search, and financial approval workflows.

## KEY FEATURES
* Multi-Agent Architecture (Manager + Specialists)

* Recipe Search by Ingredients

* Cuisine-based Recipe Filtering

* Cooking Time & Diet Preference Handling
 
* Live Ingredient Price Lookup (Web Search)

* Virtual Wallet with Balance Checks

* Human-in-the-Loop Purchase Confirmation

* DOCX-based JSON Recipe Database

* MCP Tool Server Integration

* Clean Logging & Warning Suppression

## STRUCTURE
Root Agent – <b>chef_manager</b>

Orchestrates the entire workflow and delegates tasks.

Sub-Agents
```
| Agent           | Responsibility                                 |
| --------------- | ---------------------------------------------- |
| `recipe_agent`  | Extract ingredients, preferences, find recipes |
| `cuisine_agent` | Filter recipes by cuisine                      |
| `shopper_agent` | Fetch live market prices                       |
| `wallet_agent`  | Check balance & authorize purchases            |
```
## PROJECT STRUCTURE
```
.
├── my_agent.py                     # Main multi-agent system
├── my_adk_mcp_server.py             # MCP tool server
├── name.docx                       # Recipe names & metadata (JSON)
├── wallet.json                     # Virtual wallet storage
├── .env                            # API keys
├── README.md                       # Documentation
```
## iNSTALLATION AND SETUP
1. Clone the Repository
```
git clone https://github.com/yourusername/ai-recipe-wallet-agent.git
cd ai-recipe-wallet-agent
```
2. Install dependencies
`pip install google-adk python-docx python-dotenv requests`
3. Create a .env file:
```
TAVILY_API_KEY=your_api_key_here
```
4. MCP server config
```
PATH_TO_YOUR_MCP_SERVER_SCRIPT = r"C:\absolute\path\to\my_adk_mcp_server.py"
```
## Live Market Prices

Uses Tavily Search API

Fetches prices from real retail sources

## FLOW 
```
User Query
   ↓
Chef Manager Agent
   ↓
Recipe / Cuisine Agent
   ↓
Shopper Agent (Live Prices)
   ↓
Total Cost Calculation
   ↓
Wallet Agent (Balance Check)
   ↓
User Confirmation
   ↓
Wallet Deduction
```
## Limitations

Demo-grade wallet system

DOCX JSON must be perfectly formatted

Internet required for live pricing

Not production-ready security