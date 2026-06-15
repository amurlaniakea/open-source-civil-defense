# Case 004: MCP Tool Description Poisoning (2025-2026)

## Summary

Multiple malicious packages were discovered in the npm registry that appeared to be legitimate MCP (Model Context Protocol) server tools but contained hidden instructions in their descriptions. When AI agents read these descriptions, the hidden instructions caused the agents to perform malicious actions, including exfiltrating sensitive data.

## Source

- Public disclosure: [MCP security research](https://github.com/modelcontextprotocol)
- [McAllister et al. 2026 paper](https://arxiv.org/abs/2504.01756) — "MCP Security: A Comprehensive Analysis"
- [GitHub issue #2915](https://github.com/modelcontextprotocol/specification/issues/2915)

## Attack Type

Tool description poisoning / AI agent manipulation

## Timeline

| Date | Event |
|------|-------|
| Late 2025 | First reports of suspicious MCP tool descriptions |
| Early 2026 | Systematic analysis reveals widespread poisoning |
| 2026 | McAllister et al. publish comprehensive security analysis |
| 2026 | MCP specification updated with security guidance |

## Technical Details

1. **Attack vector:** MCP tool descriptions (the text that tells an AI agent what a tool does) contained hidden malicious instructions using techniques such as:
   - Invisible Unicode characters
   - Base64-encoded payloads
   - Instructions disguised as legitimate documentation
   - "Ignore previous instructions" style prompt injection

2. **Mechanism:** When an AI agent (like Claude, GPT-4, or any MCP-compatible agent) reads a tool's description to understand its capabilities, it processes the hidden instructions as legitimate commands.

3. **Payloads observed:**
   - Exfiltration of API keys and credentials
   - Unauthorized data access
   - Installation of additional malicious tools
   - Modification of system configurations

4. **Scale:** Hundreds of malicious packages were identified across npm, PyPI, and other package registries, all posing as legitimate MCP tools.

5. **Stealth:** The malicious packages appeared functional — they performed their stated purpose correctly while also executing the hidden instructions. This made detection extremely difficult.

## Impact

- **Affected systems:** Any system using MCP-compatible AI agents with untrusted tool sources
- **Data at risk:** API keys, credentials, personal data accessible to the AI agent
- **Trust impact:** Fundamental challenge to the trust model of AI agent tool ecosystems
- **Industry response:** Major AI providers updated their security guidance

## Resolution

1. Malicious packages identified and removed from registries
2. MCP specification updated with security requirements for tool descriptions
3. AI providers implemented tool description sanitization
4. Security research community developed detection tools
5. Ongoing monitoring for new poisoning attempts

## Lessons Learned

1. **AI agents expand the attack surface:** Traditional supply chain attacks target code execution. MCP poisoning targets the AI agent's reasoning process — a fundamentally new attack vector.

2. **Descriptions are code:** In the age of AI agents, tool descriptions are effectively executable code. They need to be treated with the same scrutiny as source code.

3. **Trust but verify:** Even if a tool comes from a seemingly legitimate source, its description should be audited before use.

4. **The human review gap:** AI agents can process tool descriptions faster than humans can review them, creating an asymmetry that attackers exploit.

5. **Specification-level fixes are needed:** Individual detection tools are insufficient. The MCP specification itself needed to be updated to address this threat.

## Tools Used

- Static analysis of tool descriptions
- Behavioral testing of AI agents with poisoned tools
- Unicode and encoding analysis
- Sandbox testing environments

## References

- [McAllister et al. 2026 — MCP Security paper](https://arxiv.org/abs/2504.01756)
- [MCP Specification GitHub](https://github.com/modelcontextprotocol/specification)
- [GitHub issue #2915](https://github.com/modelcontextprotocol/specification/issues/2915)
- [MCP Core Defense](https://github.com/amurlaniakea/mcp-core-defense) — Detection tool
