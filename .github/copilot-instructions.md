# RedTeam-Tools Repository Instructions

## Project Overview
This is a **Red Team documentation repository** for a Cybersecurity Master's attack-defense exercise. It organizes penetration testing tools, tactics, and procedures (TTPs) across standard pentesting phases.

## Repository Structure
The content follows the **7-phase penetration testing methodology**:
```
Pre-Engagement/ → Planning, scope, rules of engagement
Footprinting/   → Passive reconnaissance, OSINT
Fingerprinting/ → Active scanning, enumeration, vulnerability analysis
Exploitation/   → Attack execution, privilege escalation
Post-exploitation/ → Impact assessment, lateral movement
Covering-Tracks/   → Persistence, log clearing
Reporting/         → Documentation, findings
```

## Content Conventions
When adding or editing documentation:

1. **Tool entries** should include:
   - Tool name and brief description
   - Installation command (if applicable)
   - Common usage syntax with examples
   - Links to official documentation

2. **Command examples** use fenced code blocks with shell syntax:
   ```bash
   nmap -sV -sC -oN scan.txt <target>
   ```

3. **Cross-reference** related content using relative markdown links:
   ```markdown
   See [Scanning](../Fingerprinting/Scanning.md) for port enumeration.
   ```

4. **Phase hierarchy**: Main phase file (e.g., `Fingerprinting.md`) provides overview; sub-files (`Scanning.md`, `Enumeration.md`) contain detailed TTPs.

## Key Files
- `README.md` - Main navigation hub with phase links
- `*/[PhaseName].md` - Phase overview files
- Sub-files contain specific techniques and tool guides

## Writing Style
- Action-oriented, quick-reference format suitable for live engagements
- Include both GUI and CLI approaches where applicable
- Note prerequisites (root access, specific OS, etc.)
- Mark potentially noisy/detectable techniques with warnings
