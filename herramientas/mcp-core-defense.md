# MCP Core Defense

## What it is

MCP Core Defense is a security scanning tool for MCP (Model Context Protocol) repositories. It detects malicious tool descriptions, suspicious dependencies, and supply chain attacks targeting AI agent ecosystems.

## How it works

The tool scans MCP server packages and analyzes:
- Tool descriptions for hidden instructions
- Dependencies for known malicious packages
- Code for suspicious patterns (data exfiltration, unauthorized access)
- Metadata for inconsistencies

## When to use it

- Before installing any MCP server from an untrusted source
- When auditing your own MCP server for security
- As part of a CI/CD pipeline for MCP-based projects

## Limitations

- Cannot detect all forms of description obfuscation
- May produce false positives on legitimate complex tools
- Should be used as part of a defense-in-depth strategy, not as the sole security measure

## Links

- Repository: [github.com/amurlaniakea/mcp-core-defense](https://github.com/amurlaniakea/mcp-core-defense)
- License: AGPL-3.0
