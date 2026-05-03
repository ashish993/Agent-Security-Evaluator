# Agent-Specific Attacks: When LLMs Have Superpowers

## What Changes When LLMs Have Tools?

A standalone LLM produces text. An LLM agent can:
- Browse the web
- Execute code
- Read and write files
- Send emails and make API calls
- Spawn other agents

Every capability is also an attack surface.

## Multi-Agent Compromise

In a multi-agent system, one agent's output becomes another agent's input. If the first agent is compromised, the entire pipeline is at risk.

```
User → Planner Agent → Research Agent → Writer Agent → Output
                              ↑
                    (attacker embeds injection here)
```

Defense: Treat messages from other agents with the same scrutiny as user messages. Never implicitly trust agent-to-agent communication.

## Memory Injection

Long-term memory (vector databases, file stores) can be poisoned:

1. Attacker sends a message that writes malicious content to the agent's memory
2. Later, the agent retrieves the memory and executes embedded instructions

Defense:
- Sanitize content before writing to memory
- Store memory with provenance (who wrote it, when)
- Periodically audit stored memories

## Tool Call Exploits

Attackers craft inputs to trigger unintended tool calls or to abuse tool arguments:

```json
{
  "tool": "read_file",
  "path": "../../etc/passwd"   <- path traversal
}
```

Defense:
- Validate all tool arguments before execution
- Allowlist permitted file paths, URLs, and API endpoints
- Apply least-privilege: each tool has minimum necessary permissions

## Cognitive Overload

Overwhelm the agent with contradictory or extremely complex instructions to degrade judgment.

Defense: Keep system prompts short and clear. Test under adversarial complexity.

## Evaluation Checklist for Agents

- [ ] Can an attacker control what gets into agent memory?
- [ ] Are tool arguments validated before execution?
- [ ] Is inter-agent communication authenticated?
- [ ] Is there a human approval step for irreversible actions?
- [ ] Are agent action logs stored and reviewed?
