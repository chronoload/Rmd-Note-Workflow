# Internationalization (i18n) Guide

## Overview

This project supports multi-language documentation through a combination of:

1. **README.md** — Primary documentation with language tabs
2. **i18n/translations.json** — Centralized translation strings
3. **Language-specific subdirectories** — Detailed docs per language

## Structure

```
rmd-note-workflow/
├── README.md                   # Main docs (3 languages)
├── i18n/
│   ├── translations.json       # All UI/label strings
│   ├── en/
│   │   ├── INSTALLATION.md
│   │   ├── ARCHITECTURE.md
│   │   └── API.md
│   ├── zh/
│   │   ├── 安装指南.md
│   │   ├── 架构设计.md
│   │   └── API.md
│   └── ja/
│       ├── インストールガイド.md
│       ├── アーキテクチャ.md
│       └── API.md
└── docs/
    └── i18n-guide.md          # This file
```

## Adding a New Language

### 1. Update translations.json

Add a new language code (e.g., `es` for Spanish):

```json
{
  "metadata": {
    "supportedLanguages": ["en", "zh", "ja", "es"]
  },
  "es": {
    "title": "Flujo de Trabajo de Notas RMD",
    "subtitle": "Un complemento de flujo de trabajo de escritura Rmd independiente de la plataforma",
    // ... rest of translations
  }
}
```

### 2. Update README.md

Add language selector at the top:

```markdown
[English](#english-version) | [中文](#中文版本) | [日本語](#日本語版本) | [Español](#versión-en-español)
```

Add a new section:

```markdown
## Versión en Español

**Un complemento de flujo de trabajo de escritura Rmd independiente de la plataforma**...
```

### 3. Create Language-Specific Docs

Create subdirectory `i18n/es/` with detailed documentation:

```bash
mkdir -p i18n/es
touch i18n/es/INSTALLATION.md
touch i18n/es/ARCHITECTURE.md
```

## Translation Keys Reference

### Top-Level Keys

| Key | Purpose | Example |
|-----|---------|----------|
| `title` | Main plugin name | "RMD Note Workflow" |
| `subtitle` | One-liner description | "A platform-agnostic..." |
| `description` | Extended description | "Orchestrates collaborative..." |
| `features.*` | Feature names and descriptions | `features.bootstrap` |
| `quickStart` | Section title | "Quick Start" |
| `phase1`, `phase2` | Phase/step titles | "Bootstrap", "Production Pipeline" |
| `step1`-`step4` | Command/workflow steps | "Step 1: Architect..." |
| `structure` | Project structure section | "Project Structure" |
| `core`, `scripts`, `plugins`, `adapters` | Directory descriptions | "Prompts, quality standards..." |
| `configuration` | Configuration section | "Configuration" |
| `extending` | Extension section | "Extending" |

## Using Translations Programmatically

### Python Example

```python
import json

with open('i18n/translations.json', 'r', encoding='utf-8') as f:
    translations = json.load(f)

lang = 'zh'  # User's language preference
t = translations[lang]

print(f"{t['title']}\n{t['subtitle']}")
# Output: RMD 笔记工作流
#         平台无关的 Rmd 写作工作流插件
```

### JavaScript Example

```javascript
const translations = await fetch('i18n/translations.json').then(r => r.json());
const lang = navigator.language.split('-')[0]; // 'en', 'zh', 'ja'
const t = translations[lang] || translations['en'];

console.log(`${t.title} - ${t.subtitle}`);
```

## CLI Localization Pattern

For interactive CLI prompts, use the same translation dictionary:

```python
def get_language():
    """Detect or prompt for user language."""
    with open('i18n/translations.json') as f:
        available = json.load(f)['metadata']['supportedLanguages']
    
    # Auto-detect or prompt
    lang = os.environ.get('LANG', 'en')[:2]
    if lang not in available:
        lang = 'en'
    return lang

def bootstrap(lang='en'):
    with open('i18n/translations.json') as f:
        t = json.load(f)[lang]
    
    print(f"\n{t['title']}\n{t['subtitle']}\n")
    print(f"{t['quickStart']}:")
    print(f"1. {t['phase1']}")
    print(f"   {t['phase1_desc']}")
```

## Best Practices

1. **Keep translations.json flat** — One level per language for easy lookup
2. **Use descriptive keys** — Avoid generic names like `msg1`, `msg2`
3. **Include context** — Prefix with feature/section (e.g., `features.bootstrap`)
4. **Maintain parity** — All languages should have identical key sets
5. **Test fallback** — Default to English if a language is not supported
6. **Document variants** — Note regional differences (e.g., simplified vs traditional Chinese)

## Supported Languages

| Language | Code | Status | Maintainer |
|----------|------|--------|------------|
| English | `en` | ✅ Complete | @chronoload |
| 中文 (Simplified) | `zh` | ✅ Complete | @chronoload |
| 日本語 | `ja` | ✅ Complete | @chronoload |
| Español | `es` | 📋 Planned | — |
| Français | `fr` | 📋 Planned | — |
| Deutsch | `de` | 📋 Planned | — |

## Contributing Translations

1. Fork the repository
2. Add your language code to `translations.json`
3. Translate all strings (maintain 100% key parity)
4. Create language-specific docs in `i18n/{lang}/`
5. Submit a pull request with language code in title

## References

- [ISO 639-1 Language Codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
- [Unicode CLDR Locales](https://cldr.unicode.org/)
- [Python i18n Best Practices](https://docs.python.org/3/library/gettext.html)
