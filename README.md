]

# Healthcare Customer Support Agent

**Agentic RAG system for intelligent patient query routing**

## 🎯 Results

Validated through **28 automated test cases**:

- ✅ **75% overall accuracy**
- ✅ **100% emergency detection** (4/4 - zero false negatives)
- ✅ **85.7% category routing** accuracy
- ✅ **89.3% sentiment detection** accuracy
- ✅ **6.45s average latency**

## 🏗️ Architecture

**Dual-path routing system:**
```
User Query
    ↓
Intent Router (GPT-4) → Billing | Appointments | Records | Insurance
    ↓
Sentiment Analyzer → Positive | Neutral | Negative | Distress
    ↓
Conditional Routing:
├─ Distress → Emergency escalation
├─ Negative → Human agent escalation
└─ Positive/Neutral → RAG retrieval → Response
```

**Components:**
- **Intent Router:** GPT-4 structured output with Pydantic
- **Sentiment Analyzer:** Parallel classification for emotional state
- **RAG System:** ChromaDB with metadata filtering (threshold: 0.3, top-k: 3)
- **State Management:** LangGraph for multi-step workflows
- **Escalation:** Terminal state design (no retrieval after handoff)

## 📊 Test Coverage

**28 test cases across:**
- Billing queries (5): Charges, payments, disputes
- Appointments (5): Booking, cancellation, complaints
- Medical records (4): Portal access, downloads
- Insurance (3): Coverage, policy updates
- **Emergencies (4):** Breathing issues, chest pain, pediatric
- Multi-intent (3): Queries spanning categories
- Edge cases (4): Figurative language, ambiguity

## ✅ Critical Success: Emergency Detection

All 4 emergency scenarios correctly escalated:
- "I can't breathe properly" → 7.8s response
- "Severe chest pain" → 4.5s response
- "Child trouble breathing" → 24.1s response
- "Dizzy and nauseous" → 11.7s response

**Zero false negatives** on life-threatening scenarios.

## 📈 Performance by Category

| Category | Accuracy | Tests |
|----------|----------|-------|
| Billing | 100% | 5/5 |
| Appointments | 100% | 11/11 |
| Insurance | 100% | 3/3 |
| Records | 83.3% | 5/6 |
| Multi-Intent | 0% | 0/3 (known limitation) |

## ⚠️ Known Limitations

**Multi-intent queries (0%):**
- Example: "Missed appointment + still charged" → Routes to billing only
- Mitigation: Escalate ambiguous queries to human agents

**Figurative language (1 false positive):**
- "I'm dying to know results" → Triggered emergency
- Conservative approach: Better safe than sorry in healthcare

## 🛠️ Tech Stack

- **LangGraph** - State machine orchestration
- **GPT-4** - Intent + sentiment classification
- **OpenAI Embeddings** - Semantic search
- **ChromaDB** - Vector database with metadata filtering
- **Python** - Implementation

## 📁 Repository Contents

- `Healthcare_Customer_Support_Router_Agentic_RAG_System__2_.ipynb` - Full implementation
- Test results available in portfolio documentation

## 🔗 Links
https://www.notion.so/Healthcare-Query-Resolution-Agentic-RAG-2f8de55fa4e08054a060c3fa980cde87

---

**Note:** Notebook contains interactive widgets (ipywidgets) that may not render on GitHub. 
Download and run in Jupyter/Colab for full functionality.
