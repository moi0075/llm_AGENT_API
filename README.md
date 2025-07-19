# Agent LLM avec outils

Implémentation simple d'un agent LLM capable d'utiliser des outils externes. Le système analyse les questions utilisateur, détermine quels outils sont nécessaires, et génère des réponses en français.

## Fonctionnalités

- Analyse automatique des questions pour identifier les outils requis
- Parsing JSON robuste avec gestion d'erreurs
- Système d'outils extensible
- Réponses conversationnelles en français

## Outils disponibles

- `get_weather(city)` - Informations météorologiques
- `get_time()` - Heure actuelle
- `get_pokemon_info(name)` - Données Pokémon via API publique

## Installation

```bash
git clone https://github.com/moi0075/llm_AGENT_API.git
cd llm_AGENT_API
pip install ollama requests
ollama pull phi4-mini:latest
```

## Usage

```python
from main import run_llm_agent, available_tools

# Question nécessitant plusieurs outils
response = run_llm_agent("Quelle heure est-il et quel temps fait-il à Paris ?", available_tools)

# Question simple sans outils
response = run_llm_agent("Quelle est la capitale de la France ?", available_tools)

# API externe
response = run_llm_agent("Donne-moi les stats de Pikachu", available_tools)
```

## Architecture

Le système fonctionne en 4 étapes :

1. **Analyse** - Le LLM détermine quels outils utiliser
2. **Parsing** - Extraction du JSON des instructions d'outils
3. **Exécution** - Appel des outils requis
4. **Réponse** - Génération d'une réponse naturelle en français

## Ajout d'outils

```python
def nouvel_outil(param):
    return "résultat"

available_tools["nom_outil"] = {
    "description": "Description de l'outil",
    "format": '{"name": "nom_outil", "params": ["param"]}',
    "tool_function": nouvel_outil
}
```

## Modèles testés

- phi4-mini:latest
- gemma3n:e2b
- qwen2.5:3b

## Notes

Implementation alternative à LangChain avec un focus sur la simplicité et la stabilité pour les petits modèles. Workflow transparent sans abstractions complexes.
