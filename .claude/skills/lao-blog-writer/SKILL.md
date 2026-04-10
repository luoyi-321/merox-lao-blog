---
name: lao-blog-writer
description: >
  ຂຽນ blog ເທັກນິກພາສາລາວໃໝ່ສຳລັບ merox-erudite.
  ສ້າງໄຟລ໌ MDX ທີ່ຖືກຕ້ອງ ລວມທັງ frontmatter, Lao-English mixed content,
  Callout components, code blocks, ແລະ ຕາຕະລາງ.
  ຮອງຮັບ URL sources — ໃຊ້ WebFetch ດຶງເນື້ອຫາຈາກ link ກ່ອນຂຽນ.
  ວາງໄຟລ໌ທີ່ src/content/blog/{slug}/index.mdx.
argument-hint: "<topic> [source-url-1] [source-url-2] ..."
user-invocable: true
metadata:
  version: "1.1"
  author: laligence
  tools: [WebFetch, WebSearch]
  output: "src/content/blog/{slug}/index.mdx"
---

## Overview

Skill ນີ້ຂຽນ blog ເທັກນິກພາສາລາວ (Lao-first, technical English mixed in) ສຳລັບ
Laligence AI Research blog ໃນ project merox-erudite (Astro + MDX).
ທຸກ post ຕ້ອງຕາມ convention ດ້ານລຸ່ມ ຢ່າງເຂັ້ມງວດ.

---

## Blog File Convention

### ໂຄງສ້າງໄຟລ໌

```
src/content/blog/{slug}/
└── index.mdx
```

- `{slug}` = lowercase-hyphen, ພາສາອັງກິດ, ສັ້ນ, ກ່ຽວຂ້ອງກັບຫົວຂໍ້
- ຕົວຢ່າງ: `lao-tts-benchmark`, `attention-mechanism-explained`, `lao-nlp-tokenizer`

### Frontmatter Template

```mdx
---
title: '[ຫົວຂໍ້ເປັນພາສາລາວ]'
description: '[ອະທິບາຍ 1-2 ປະໂຫຍກ, ລາວ, ໃສ່ keywords ຫຼັກ]'
date: YYYY-MM-DD
tags: ['tag1', 'tag2', 'tag3']    # lowercase-hyphen, 3-8 tags
authors: ['laligence']
---
```

### Imports ທີ່ຕ້ອງໃສ່ (ຫຼັງ frontmatter)

```mdx
import Callout from '@/components/Callout.astro'
```

### Author Header (ຫຼັງ import ທຸກໄຟລ໌)

```mdx
<div style="display: flex; align-items: center; gap: 12px; margin-bottom: 24px;">
  <img src="/merox-lao-blog/laligence-icon.svg" alt="Laligence" style="width: 40px; height: 40px;" />
  <span style="font-size: 0.85rem; color: #888;">Laligence AI Research · Vientiane, Laos</span>
</div>
```

---

## ກົດການຂຽນ Content

### 1. ພາສາ
- **ຫຼັກ**: ລາວ
- **ຄຳສັບເທັກນິກ**: ໃຫ້ອ່ານດ້ວຍ English (ເຊັ່ນ: model, fine-tuning, benchmark, pipeline, token)
- **ຄຳອະທິບາຍ**: ລາວທັງໝົດ
- ຫ້າມ mix ພາສາໃນ mid-sentence ໂດຍໄມ່ຈຳເປັນ — ໃຊ້ English ສຳລັບ noun ທີ່ 업lade ຍາວ

### 2. Headers
- ເລີ່ມທີ່ `##` (ຫ້າມໃຊ້ `#` single)
- `###` ສຳລັບ sub-section
- ຫົວຂໍ້ຫຼັກ: ລາວ, sub-section ອາດ mix

### 3. Section Dividers
ໃຊ້ `---` ແຍກລະຫວ່າງ sections ໃຫຍ່

### 4. Callout Types

| Type | ໃຊ້ເມື່ອ |
|------|---------|
| `info` | ຂໍ້ມູນເສີມ, ຂໍ້ແນະນຳ background |
| `tip` | best practice, shortcut, ຄຳແນະນຳ |
| `warning` | ຂໍ້ລະວັງ, ຄວາມຜິດພາດທີ່ພົບເລື້ອຍ |

```mdx
<Callout type="info">
ເນື້ອຫາ...
</Callout>
```

### 5. Code Blocks
- ໃສ່ language tag ທຸກຄັ້ງ: ` ```python`, ` ```bash`, ` ```yaml`, ` ```typescript`
- ສຳລັບ diagram / ASCII art ໃຊ້ ` ``` ` (ບໍ່ມີ language tag)

### 6. ຕາຕະລາງ (Tables)
ໃຊ້ markdown table ສຳລັບ comparison, metrics, ລາຍການ structured

### 7. Footer (ທ້າຍທຸກ post)

```mdx
---

*ຂຽນໂດຍ Laligence AI Research Team · Vientiane, Laos*
```

---

## ຂັ້ນຕອນດຳເນີນການ (Step-by-Step)

1. **ຮັບ topic + sources** ຈາກຜູ້ໃຊ້ (Lao ຫຼື English) — sources ອາດເປັນ URL ຫຼືບໍ່ມີກໍໄດ້
2. **Fetch sources** (ຖ້າຜູ້ໃຊ້ໃຫ້ URL ມາ):
   - ໃຊ້ `WebFetch` ດຶງເນື້ອຫາຈາກທຸກ URL ທີ່ໃຫ້ມາ
   - ອ່ານ + ສະຫຼຸບຂໍ້ມູນຫຼັກຈາກແຕ່ລະ source
   - ຖ້າ source ເປັນ paper/doc ທາງເທັກນິກ: ດຶງ metrics, method, ແລະ result ອອກ
   - ຖ້າຍັງຕ້ອງການຂໍ້ມູນເພີ່ມ: ໃຊ້ `WebSearch` ຊອກຫາ reference ເສີມ
3. **ກຳໜົດ slug** — lowercase-hyphen English, ສັ້ນ, ຊັດ
4. **ວາງແຜນໂຄງສ້າງ** — ລາຍຊື່ sections ຫຼັກ (3-7 sections) ໂດຍອີງຈາກ source content
5. **ຂຽນ frontmatter** — title ລາວ, description ລາວ, date = ວັນນີ້, tags relevant
6. **ຂຽນ content**:
   - ເລີ່ມດ້ວຍ "X ຄືຫຍັງ?" ຫຼື "ເປັນຫຍັງ X ສຳຄັນ?" ສຳລັບ intro
   - ໃຊ້ Callout `info` ໃສ່ context ສຳຄັນ
   - ໃຊ້ code block ສຳລັບ technical examples
   - ໃຊ້ table ສຳລັບ comparison ຫຼື metrics
   - ໃຊ້ Callout `tip` ສຳລັບ best practice
   - ໃຊ້ Callout `warning` ສຳລັບ gotchas
   - ຖ້າມີ source URLs: ໃສ່ section "ແຫຼ່ງຂໍ້ມູນ" ທ້າຍສຸດ (ກ່ອນ footer)
   - ຈົບດ້ວຍ "ສະຫຼຸບ" section + footer
7. **ສ້າງໄຟລ໌** ທີ່ `src/content/blog/{slug}/index.mdx`

---

## ການ Fetch Source URLs

### ໃຊ້ WebFetch ແນວໃດ

```
WebFetch(url="https://example.com/paper")
→ ໄດ້ຮັບ: title, abstract, method, results, conclusion
→ ສະຫຼຸບ: ຂໍ້ມູນທີ່ໃຊ້ໃນ blog ໄດ້
```

### ກົດ

| ສະຖານະການ | ວິທີ handle |
|-----------|------------|
| URL ໃຊ້ໄດ້ | Fetch → ສະຫຼຸບ → ຂຽນ content ຈາກ source |
| URL ໃຊ້ບໍ່ໄດ້ (404, timeout) | ແຈ້ງຜູ້ໃຊ້ + ດຳເນີນໂດຍໃຊ້ knowledge ທີ່ມີ |
| Source ເປັນ PDF / paper | ດຶງ abstract + key findings + metrics |
| Source ເປັນ GitHub repo | ດຶງ README: purpose, usage, benchmark ຖ້າມີ |
| Source ເປັນ blog/article | ດຶງ key concepts + ຕົວຢ່າງ code ຖ້າມີ |

### ໂຄງສ້າງ "ແຫຼ່ງຂໍ້ມູນ" Section (ເພີ່ມຖ້າມີ source)

```mdx
## ແຫຼ່ງຂໍ້ມູນ

- [ຊື່ source 1](URL1) — ອະທິບາຍສັ້ນວ່າ source ນີ້ໃຫ້ຫຍັງ
- [ຊື່ source 2](URL2) — ອະທິບາຍສັ້ນ
```

---

## Tags Reference

ໃຊ້ tags ທີ່ໃຊ້ຢູ່ແລ້ວໃຫ້ consistent:

```
lao-ai, lao-nlp, speech, asr, tts, whisper, benchmark, evaluation,
tokenizer, embedding, fine-tuning, python, pytorch, fastapi, nextjs,
claude, ai-agent, skill-md, prompt-engineering, data-sparsity,
deep-learning, transformer, attention, neural-networks
```

---

## ໂຄງສ້າງ Content ທີ່ແນະນຳ

### Blog ປະເພດ "Tutorial / How-to"

```
## X ຄືຫຍັງ?
## ເປັນຫຍັງຕ້ອງໃຊ້ X?
## ໂຄງສ້າງ / Architecture
## ຂັ້ນຕອນ Step-by-Step
  ### ຂັ້ນຕອນທີ 1: ...
  ### ຂັ້ນຕອນທີ 2: ...
## ຕົວຢ່າງຈິງ
## ຂໍ້ຜິດພາດທີ່ຄວນຫຼີກລ້ຽງ
## ສະຫຼຸບ
```

### Blog ປະເພດ "Benchmark / Evaluation"

```
## X ແລະ Y ຄືຫຍັງ?
## ເປັນຫຍັງຕ້ອງ Benchmark?
## Dataset
## Metrics ທີ່ໃຊ້
## ຜົນທົດສອບ (ຕາຕະລາງ)
## ວິເຄາະຜົນ
## ສະຫຼຸບ
```

### Blog ປະເພດ "Concept Explanation"

```
## X ຄືຫຍັງ?
## ວິທີການເຮັດວຽກ
## ໃຊ້ X ໃນ Context ລາວ
## ຕົວຢ່າງ / Case Study
## ສິ່ງທ້າທາຍ
## ສະຫຼຸບ
```

---

## ຂໍ້ຈຳກັດ

- ຫ້າມໃຊ້ `#` single-level header (ຕ້ອງ `##` ຂຶ້ນໄປ)
- `authors` ຕ້ອງ `['laligence']` ສະເໝີ
- `date` ຕ້ອງ format `YYYY-MM-DD`
- ຕ້ອງ import Callout ທຸກ post (ເຖິງບໍ່ໃຊ້ ໃຫ້ import ໄວ້)
- content ຄວນ 500-2000 ຄຳ — ບໍ່ສັ້ນ / ຍາວເກີນໄປ
- ຫ້າມສ້າງໄຟລ໌ ຖ້າ slug ຊ້ຳກັບ folder ທີ່ມີຢູ່ແລ້ວ (ກວດກ່ອນ)

---

## ຕົວຢ່າງ (Example Output Skeleton)

```mdx
---
title: 'ຫົວຂໍ້ Blog ເປັນລາວ'
description: 'ອະທິບາຍສັ້ນ ລາວ ປະມານ 1-2 ປະໂຫຍກ'
date: 2026-04-06
tags: ['lao-ai', 'relevant-tag']
authors: ['laligence']
---

import Callout from '@/components/Callout.astro'

<div style="display: flex; align-items: center; gap: 12px; margin-bottom: 24px;">
  <img src="/merox-lao-blog/laligence-icon.svg" alt="Laligence" style="width: 40px; height: 40px;" />
  <span style="font-size: 0.85rem; color: #888;">Laligence AI Research · Vientiane, Laos</span>
</div>

## X ຄືຫຍັງ?

ເນື້ອຫາ intro...

<Callout type="info">
ຂໍ້ມູນສຳຄັນ...
</Callout>

---

## ວິທີການເຮັດວຽກ

...

---

## ສະຫຼຸບ

...

---

*ຂຽນໂດຍ Laligence AI Research Team · Vientiane, Laos*
```
