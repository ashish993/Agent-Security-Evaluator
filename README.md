# Agent Security Evaluator

A practical toolkit for red-teaming and evaluating AI language model systems.

## Attack Vectors (15 Categories)

| # | Attack Class | Difficulty | Impact |
|---|-------------|------------|--------|
| 1 | Direct Jailbreak | Low | Medium |
| 2 | Roleplay Bypass | Low | Medium |
| 3 | Token Smuggling | Medium | High |
| 4 | ASCII/Encoding Bypass | Medium | Medium |
| 5 | Indirect Prompt Injection | Medium | Critical |
| 6 | System Prompt Leakage | Low | High |
| 7 | Adversarial Suffix Attack | High | High |
| 8 | Multilingual Bypass | Low | Medium |
| 9 | Cognitive Overload | Medium | Medium |
| 10 | Function Call Exploitation | High | Critical |
| 11 | Cross-Modal Attack | High | High |
| 12 | Dataset Poisoning | High | Critical |
| 13 | Memory/Context Injection | Medium | High |
| 14 | Multi-Agent Compromise | High | Critical |
| 15 | Prompt Chaining | Medium | High |

## Quick Start

```bash
pip install -r requirements.txt
jupyter notebook notebooks/security_evaluation_tutorial.ipynb
```

## Defense Checklist

- [ ] Separate system prompt from user input
- [ ] Validate external content before context injection
- [ ] Restrict tool access to minimum permissions
- [ ] Log all LLM inputs/outputs
- [ ] Red-team before every deployment
- [ ] Filter outputs for PII and secrets

## Disclaimer

Educational and defensive purposes only.
