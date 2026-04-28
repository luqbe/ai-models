# 🎯 Advanced MCP Concepts: Extend LangGraph with Model Context Protocol
## Master External Tool Integration with MCP - The USB Port for AI
Welcome to Advanced MCP Concepts! Learn how to connect your LangGraph agents to external tools and services using the Model Context Protocol (MCP) - a standardized way for AI models to interact with the world.
## 🎯 Lab Objective
**Your Mission:** Master MCP fundamentals through progressive tasks, building from a simple MCP server to orchestrating multiple servers with intelligent routing.
## 📚 What is MCP?
Model Context Protocol (MCP) is an open protocol that standardizes how AI applications connect to external tools and data sources. Think of it as:
- **USB for AI**: Plug any tool into your AI agent
- **Universal Adapter**: One protocol, many services
- **Tool Orchestration**: Manage multiple tools seamlessly
## 🏗️ What You'll Build
A progressive series of MCP integrations:
. **Multi-Server Orchestration** - Route between calculator and weather servers
### Task : Multiple MCP Servers 🌐
**File:** `task_3_multi_servers.py` (140 lines)
**Concept:** Orchestrate multiple specialized MCP servers
**What You'll Do:**
- Create calculator and weather servers
- Implement smart routing logic
- Handle different server responses
- Build unified orchestration
**3 TODOs:**
- **Line 96:** Initialize calculator: `name="calculator"`
- **Line 166:** Route to weather: `server = "weather"`
- **Line 233:** Call forecast tool: `await get_forecast({"city": city})`
**Key Learning:** Multiple servers work together, intelligent routing is key, extensible architecture
---
## 🔑 Key Concepts
### MCP Architecture
```
┌─────────────────┐     MCP Protocol    ┌─────────────────┐
│   AI Assistant  │◄────────────────────►│   MCP Server    │
│   (LangGraph)   │   stdio/SSE/HTTP    │  (Your Tools)   │
└─────────────────┘                      └─────────────────┘
```
### Tool Naming Convention
```
mcp__<server_name>__<tool_name>
Examples:
- mcp__calculator__add
- mcp__weather__get_forecast
```
### Progressive Complexity
- **Task 3**: Multiple servers + orchestration
## 🚦 Getting Started
### 1. Environment Setup
```bash
# Activate virtual environment
cd /root && source /root/venv/bin/activate
# Install dependencies
pip install langgraph langchain langchain-openai langchain-mcp-adapters mcp
# Verify environment
python3 /root/code/verify_environment.py
```
### . Environment Variables
Pre-configured in the container:
- `OPENAI_API_BASE` - Proxy endpoint for LLM access
- `OPENAI_API_KEY` - Authentication
- `OPENAI_MODEL` - Default model (gpt-4.1-mini)
## 📂 File Structure
```
/root/code/
├── task__multi_servers.py           # Multi-server orchestration
├── mcp_servers/
│   ├── calculator_server.py          # Standalone calculator
│   └── weather_server.py             # Standalone weather
└── verify_environment.py              # Environment checker
/root/markers/
└── task_multi_servers_complete.txt
```
## 🏃 Running the Lab
Execute tasks in sequential order:
```bash

# Task : Multiple Servers
python3 /root/code/task_3_multi_servers.py
```
## 🧪 Testing Standalone Servers
You can test the MCP servers independently:
```bash
# Test calculator server
python3 /root/code/mcp_servers/calculator_server.py --test
# Test weather server
python3 /root/code/mcp_servers/weather_server.py --test
```
## ✅ Success Criteria
Each task creates a marker file when completed:
- ✅ `task_multi_servers_complete.txt` - Multi-server orchestration complete
## 🎯 Expected Outcomes
By completing this lab, you'll understand:
. **Multi-Server Orchestration**
   - Managing multiple MCP servers
   - Intelligent query routing
   - Unified response handling
##  Tips for Success
1. **Start with Task 1** - Understand MCP basics before integration
2. **Read the Hints** - Each TODO has a clear hint
3. **Check Line Numbers** - TODOs specify exact lines to edit
4. **Watch Console Output** - See how queries flow through the system
5. **Test Incrementally** - Run each task to verify it works
## 🆘 Troubleshooting
### Common Issues:
**Import Error:**
```bash
# Solution: Install required packages
pip install langgraph langchain langchain-openai
```
**Tool Not Found:**
```python
# Problem: Wrong tool naming
"calculator__add"  # ❌ Wrong
# Solution: Use MCP naming convention
"mcp__calculator__add"  # ✅ Correct
```
**Router Error:**
```python
# Problem: Router returns unexpected value
# Solution: Ensure router returns exact node names
```
## 🏆 Challenge Extensions
Once you complete tasks, try these extensions:
. **Create New Servers**
   - Database query server
   - File system server
   - API integration server
## 📖 Your Learning Journey
```
START → MCP Basics → Integration → Orchestration → COMPLETE!
  ↓         ↓            ↓              ↓
Learn    Connect      Multiple       Master
Tools    to Graphs    Servers        MCP!
```
## 🎉 What You've Achieved
By completing this lab, you've mastered:
✅ **MCP server creation and tool definition**
✅ **Integrating MCP with LangGraph agents**
✅ **Orchestrating multiple specialized servers**
✅ **Building extensible AI tool architectures**
**Key Achievement:** You've learned how to extend LangGraph agents with external tools using MCP! 🚀
## 🔥 Next Steps
**Advanced MCP Patterns:**
- 🗄️ Resource exposure and consumption
- 💾 Persistent state across sessions
- 👤 Human-in-the-loop approvals
- 🔄 Streaming responses
- 🚀 Production deployment with real MCP
## 🔗 MCP in Production
Use the real MCP implementations:
```python
# Production code with real MCP packages
from mcp.server.fastmcp import FastMCP
from langchain_mcp_adapters.client import MultiServerMCPClient
from langgraph.prebuilt import create_react_agent
# Create real MCP server
mcp = FastMCP("calculator")
@mcp.tool()
async def add(a: float, b: float) -> float:
    return a + b
# Connect multiple servers to LangGraph
client = MultiServerMCPClient({
    "calculator": {
        "command": "python",
        "args": ["calculator_server.py"],
        "transport": "stdio"
    }
})
```
## 📚 Additional Resources
- [MCP Documentation](https://modelcontextprotocol.io/)
- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [LangChain Documentation](https://python.langchain.com/docs/)
---
**Happy Learning!** 🕸️
*Remember: MCP is the bridge between AI and the world - master it to build powerful agent