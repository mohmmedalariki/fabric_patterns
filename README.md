# Custom Fabric Patterns

This repository contains custom patterns designed to be used with [Fabric](https://github.com/danielmiessler/fabric), an open-source framework for augmenting humans using AI.

Fabric uses "patterns" (highly optimized system prompts) to process input data (from the clipboard, files, or pipelines) and return structured, high-quality output.

## Included Patterns

### 1. `bnote` (Bug Bounty Obsidian Notes)

**Purpose:**
Instantly converts raw, unstructured bug bounty writeups, vulnerability disclosures, or recon data into a highly organized, deeply-linked Markdown note tailored for an Obsidian vault.

**Features:**

- Automatically generates YAML frontmatter with title, date, and nested tags (e.g., `#bugbounty/recon`).
- Extracts the core vulnerability overview, exact payloads, vulnerable parameters, step-by-step methodology, and tools used.
- Strategically wraps concepts, methodologies, and tools in Obsidian wiki-links (`[[Concept]]`) to automatically populate your knowledge graph.

**Usage Example:**

```bash
# Copy a writeup to your clipboard, then run:
pbpaste | fabric -p bnote > my_finding.md
```

### 2. `tool` (CLI Tool Manual Explainer)

**Purpose:**
Takes raw, dense command-line manual pages or help output (e.g., from `nmap -h`, `ffuf -h`) and translates them into a clear, structured, beginner-friendly guide.

**Features:**

- Strips away jargon and groups flags logically by their function.
- Provides a real-world, copy-pasteable example command for every flag.
- Explains the exact scenario / "when to use" context for each flag.
- Includes a "Beginner Essentials" list and a "Common Mistakes" warning section.

**Usage Example:**

```bash
# Pipe the help output of any tool directly into the pattern:
nmap -h | fabric -p tool
```

## How to Install

1. Make sure you have [Fabric installed and configured](https://github.com/danielmiessler/fabric).
2. Clone this repository or download the specific pattern folder.
3. Copy the pattern folder into your local Fabric patterns directory:

   ```bash
   cp -r bnote ~/.config/fabric/patterns/
   cp -r tool ~/.config/fabric/patterns/
   ```

4. Verify the installation by running:

   ```bash
   fabric -l | grep -E 'bnote|tool'
   ```
