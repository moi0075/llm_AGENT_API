# LLM Agent API

Agent LLM personnalisé en Python utilisant des outils externes pour répondre intelligemment aux questions.

## 🚀 Fonctionnalités

- **Agent intelligent** : Détermine automatiquement les outils nécessaires
- **Système modulaire** : Facilement extensible
- **Parsing robuste** : Extraction JSON fiable
- **Réponses naturelles** : En français, conversationnelles
- **Alternative à LangChain** : Plus stable avec les petits modèles

## 🛠️ Outils

- `get_weather(city)` : Météo pour une ville
- `get_time()` : Heure actuelle

## ⚡ Installation rapide

```bash
git clone https://github.com/moi0075/llm_AGENT_API.git
cd llm_AGENT_API
pip install ollama requests langchain-community
ollama pull gemma3n:e2b
```

## 🚀 Usage

```python
from main import run_llm_agent, available_tools

# Question avec outils
response = run_llm_agent("Météo à Paris et heure actuelle ?", available_tools)

# Question simple
response = run_llm_agent("Combien font 2+2 ?", available_tools)
```

## 🏗️ Architecture

1. **Analyse** → 2. **Parsing JSON** → 3. **Exécution outils** → 4. **Réponse naturelle**

## 📊 vs LangChain

| Aspect      | Notre implémentation     | LangChain             |
| ----------- | ------------------------ | --------------------- |
| Stabilité   | ✅ Stable petits modèles | ❌ Parsing errors     |
| Contrôle    | ✅ Total                 | ❌ Complexe           |
| Performance | ✅ Moins de boucles      | ❌ Boucles fréquentes |

---

**Résultat** : Plus stable et précis que LangChain avec les petits modèles. Code simple et workflow contrôlé.
