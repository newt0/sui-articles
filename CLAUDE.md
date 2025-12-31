# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a documentation repository for translating Sui Foundation Blog articles from English to Japanese. It contains:

- **English source articles** (`en/`) - Original blog posts from Sui Foundation Blog
- **Japanese translations** (`ja/`) - Translated versions (currently empty, to be populated)
- **Translation prompts** (`prompt/`) - Guidelines and terminology for translation work

## Repository Structure

```
sui-articles/
├── en/                          # English source articles from Sui Foundation Blog
│   └── *.md                     # Individual blog post markdown files
├── ja/                          # Japanese translations (target directory)
├── prompt/
│   └── translate-sui-blog.md    # Translation guidelines and terminology reference
└── README.md
```

## Translation Workflow

### Translation Guidelines

The file `prompt/translate-sui-blog.md` contains comprehensive translation guidelines, including:

- **Markdown structure preservation** - Do not add H1 if not specified in the original
- **Code handling** - Preserve inline code and code blocks without translation
- **Terminology standards** - Extensive lists of Sui-specific terms and their handling:
  - Terms to keep in English (e.g., Sui Network, Move, Object, PTB, zkLogin)
  - Terms to convert to katakana (e.g., transaction → トランザクション, gas → ガス)
  - Specified translations (e.g., consensus → コンセンサス, finality → ファイナリティ)

### Key Translation Principles

1. **Target audience**: Developers, engineers, and researchers interested in Sui and Move language
2. **Style**: Professional yet approachable Japanese using です・ます form
3. **Technical accuracy**: Maintain precision while ensuring natural Japanese expression
4. **Sui/Move concepts**: Provide brief explanations for Sui-specific concepts (Object model, Programmable Transaction Block) on first mention

### Terminology Categories

The translation prompt categorizes terms into four groups:

1. **Sui Network/Protocol** - Sui, Narwhal, Bullshark, Mysticeti, Validator, Checkpoint, etc.
2. **Move Language/Object Model** - Move, Object ID, Shared Object, Owned Object, Capability, Witness Pattern, etc.
3. **Sui Features** - zkLogin, Sui Kiosk, SuiNS, DeepBook, Walrus, Sponsored Transaction, etc.
4. **Blockchain General** - Proof of Stake, dApp, DeFi, NFT, Smart Contract, etc.

## Working with Articles

### Article Format

English articles in `en/` follow this general structure:
- Title with source URL link
- Header with metadata (author, images)
- Body content with technical explanations
- May include inline code and code blocks (typically Move language)

### When Adding New Articles

1. Place English source in `en/` directory with descriptive filename (e.g., `ai-agents-explained.md`)
2. Use kebab-case for filenames
3. Preserve original markdown structure including links and images
4. When translating, place Japanese version in `ja/` with the same filename

### When Translating Articles

1. Read `prompt/translate-sui-blog.md` thoroughly first
2. Review the entire article to understand context before translating
3. Apply terminology guidelines consistently
4. Preserve all markdown formatting, code blocks, and inline code
5. Do not add explanatory text or instructions - output only the translation
6. Review for consistency and quality after translation

## Git Workflow

This is a git repository. When working with articles:
- Create descriptive commit messages for translations or article additions
- Branch name: currently on `main`
- Keep English and Japanese versions synchronized by filename
