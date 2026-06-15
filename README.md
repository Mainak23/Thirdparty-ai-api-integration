# UniChain Gateway (Project HandshakeAI)

An adaptable, lightweight LangChain abstraction client engineered to bridge the gap between enterprise security architectures and modern agentic AI workflows.

## 🚀 The Challenge & Solution

**The Problem:** Modern enterprises route large language model (LLM) traffic through unified API firewalls or secure gateways to enforce data security, context filtering, and compliance boundaries. However, these firewalls often strip payload metadata, modify standard message parameters, or restrict structural formats. This environment causes LLMs to **lose or break their native tool-calling capacity**, fracturing the essential two-way handshake required by autonomous agents.

**The Solution:** `UniChain Gateway` acts as a resilient intelligence wrapper directly inside LangChain's native message structure. It dynamically alters its formatting logic on the fly depending on your network's topology—ensuring uninterrupted tool execution and functional automation without compromising corporate data compliance.

---

## 🛠️ Key Architectural Features

* **Dynamic Payload Fluidity:** Automatically converts tool definitions between standard OpenAI nested formats (`tools`) and flat enterprise schema blocks (`functions`) depending on backend capability.
* **Authentication Resilience:** Seamlessly adapts to strict header policies, abstracting variable API keys and standard/raw authorization token configurations.
* **State & Flow Normalization:** Normalizes downstream firewall text responses and legacy structured function arrays back into clean LangChain execution chains.

---

## 📋 Prerequisites & Installation

To run this implementation within your local development workspace or inside a Google Colab notebook, ensure you install the required core packages:

```bash
pip install langgraph requests pydantic langchain-core

💻 Quick Start: Google Colab Setup

Paste this fully self-contained reactive agent block into a code cell. Ensure your access credential token is mapped securely to your environment variables:

import json
import requests
from typing import List, Any, Iterator, Optional, Dict, Sequence, Union
from langchain_core.language_models.chat_models import BaseChatModel
from langchain_core.messages import BaseMessage, AIMessage, HumanMessage, SystemMessage
from langchain_core.outputs import ChatResult, ChatGeneration
from langchain_core.tools import tool
from langgraph.prebuilt import create_react_agent
from pydantic import Field

# 1. Instantiate the Flexible Universal Framework
llm = UniversalGatewayChatModel(
    model_name="default",
    base_url="[https://api.llm7.io/v1](https://api.llm7.io/v1)",
    api_key="YOUR_SECURE_GATEWAY_TOKEN",
    is_openai_compatible=True # Toggle to False if hitting a hardened legacy proxy
)

# 2. Define Your Execution Tool Asset
@tool
def multiply(a: int, b: int) -> int:
    """Multiply two integers together accurately."""
    return a * b

# 3. Compile the Complete Two-Way Handshake Loop
agent_executor = create_react_agent(llm, tools=[multiply])

# 4. Trigger Execution Trace
response = agent_executor.invoke({"messages": [("user", "What is 15 times 27?")]})
print("Final Synthesis:", response["messages"][-1].content)


| Method / Variable -----| Purpose----------------------------------------------------------------------------------------------|
| :--- ------------------| :----------------------------------------------------------------------------------------------------|
| `is_openai_compatible` | If `True`, formats schemas inside modern arrays. If `False`, uses classic flat structural functions. 
| `use_bearer_prefix`    | Controls whether the token requires standard `Bearer ` appending configurations. 
| `_convert_messages()`  | Serializes stateful objects down to raw dictionary structures acceptable by network firewalls. 
| `_generate()`          | Coordinates the core synchronous execution request thread and maps outbound API outputs. 
| `_stream()`            | Keeps connection pipes open for live word-by-word token printing. 
