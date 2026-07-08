# 🚀 LangGraph Learning

A hands-on repository for learning **LangGraph**, the framework for building **stateful AI agents** and **multi-step workflows** on top of LangChain.

This repository contains examples ranging from basic graphs to AI agents with tools, memory, and conditional execution.

---




## 📚 Topics Covered

- Introduction to LangGraph
- StateGraph
- State Management
- Nodes
- Edges
- Conditional Edges
- START & END Nodes
- Tool Calling
- Chatbots

---

## 🧩 Core Concepts

### State

State is the shared data that flows through every node.

```python
state = {
    "messages": [],
    "answer": "",
    "documents": []
}
```

---

### Nodes

A node is simply a Python function that performs one task.

```python
def chatbot(state):
    return {"messages": [llm.invoke(state["messages"])]}
```

---

### Edges

Edges define the execution flow.

```python
graph.add_edge("chatbot", "tools")
```

---

### Conditional Edges

Conditional edges decide which node to execute next based on the current state.

```python
graph.add_conditional_edges(
    "chatbot",
    tools_condition
)
```

---

## 🏗️ Workflow Example

```
           User
             │
             ▼
          START
             │
             ▼
        Chatbot Node
             │
      Tool Required?
        /         \
      Yes         No
       │           │
       ▼           ▼
   Tools Node     END
       │
       ▼
    Chatbot
       │
       ▼
      END
```

---
