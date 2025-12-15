# ideas-drafts

Explorations, architectural proposals, and conceptual prototypes.

---

## Projects

| Project | Status | Stack | Description |
|---------|--------|-------|-------------|
| [Probabilistic UX Friction Analysis](./Emotion-UX-Analysis/) | 🔬 Exploration | Hume AI, LangGraph, RAG, XGBoost | Multimodal friction detection via expressive cues and interaction patterns |
| [Controlled Intuition Engine](./Controlled-Intuition-Engine/) | 💡 Conceptual | LangGraph, RAG, HPC Integration | Agentic hypothesis pre-layer for optimizing costly scientific discovery pipelines |
| [Blendr Assist](./Blender-Assist/) | 🎨 Conceptual | Gemini, Blender MCP, LangGraph | Multi-agent pipeline for 2D flash to 3D model conversion via MCP orchestration |

---

## Philosophy

These drafts are not production-ready code. They are **architectural sketches** — structured ideas before implementation.

Goals:
- Formalize thinking before coding
- Document technical choices and their justifications
- Explore non-conventional approaches

---

## Common Patterns

Across these projects, recurring architectural patterns emerge:

| Pattern | Description | Used In |
|---------|-------------|---------|
| **Probabilistic Framing** | Output probabilities, not certainties | UX Friction, CIE |
| **Human-in-the-Loop** | Checkpoints for human validation | UX Friction, Blendr Assist |
| **RAG as Shared Knowledge** | Vector DB accessible by multiple agents | All three |
| **MCP as Tool Abstraction** | Unified interface to external tools | Blendr Assist |
| **Feedback Loops** | Iterative refinement via comparison | CIE, Blendr Assist |

---

## Resources

- [Papers & References](./ressources/papers.md)
- [Multi-Agent Patterns](./ressources/multi-agent-patterns.md)
