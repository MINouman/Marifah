# Marifah
> A conservative, evidence-driven Islamic reasoning assistant based on the Qur'an, authentic Hadith, and classical Fiqh methodology across all four Sunni madhhabs.

**Current Phase:** Data Collection

---

## Table of Contents

- [Overview](#overview)
- [What This System IS and IS NOT](#what-this-system-is-and-is-not)
- [Core Objectives](#core-objectives)
- [Methodology](#methodology)
- [Architecture](#architecture)
- [Data Strategy](#data-strategy)
- [Madhhab Implementation](#madhhab-implementation)
- [Reasoning Philosophy](#reasoning-philosophy)
- [Technical Stack](#technical-stack)
- [Scholar Testing & Feedback](#scholar-testing--feedback)
- [Safety & Ethics](#safety--ethics)
- [Current Status](#current-status)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Disclaimer](#disclaimer)

---

## Overview

This project builds a scholarly reasoning assistant that helps users understand Islamic rulings and scholarly reasoning based on:

- **The Qur'an**
- **Authentic Hadith**
- **Classical Fiqh**
- **Usūl al-Fiqh (Islamic Legal Theory)**
- **All four Sunni madhhabs** (Hanafi, Shafi'i, Maliki, Hanbali)

The system presents structured scholarly reasoning, clearly shows evidence, differences of opinion (ikhtilāf), and levels of certainty. It explicitly states limitations when a question requires human ijtihād.

### Guiding Principles

- **Correctness over fluency**
- **Traceability over creativity**
- **Scholarly methodology over model size**
- **No public release without scholarly approval**

---

## What This System IS and IS NOT

### The System IS:

✅ A scholarly reasoning assistant  
✅ Madhhab-aware and evidence-first  
✅ Conservative and self-restraining  
✅ Transparent about certainty levels  
✅ Designed to present classical methodology  

### The System IS NOT:

❌ A mujtahid or fatwa authority  
❌ A replacement for scholars  
❌ A source of free opinion  
❌ Authorized to issue religious rulings  

This distinction is enforced both technically and linguistically throughout the system.

---

## Core Objectives

1. **Preserve classical Islamic methodology** in AI form
2. **Prevent hallucination, overconfidence, and opinion mixing**
3. **Handle new or uncommon questions** through usūl-based reasoning, not guessing
4. **Maintain full auditability** of answers
5. **Keep cost low** and development solo-friendly
6. **Ensure scholarly oversight** before any public deployment

---

## Methodology

The system follows **classical Islamic scholarly reasoning**, not AI creativity.

### Evidence Hierarchy

1. **Qur'an** (explicit texts)
2. **Authentic Hadith** (Sahih > Hasan > Da'if)
3. **Ijmā' (Scholarly Consensus)**
4. **Qiyās (Valid Analogy)** - only when justified by usūl
5. **Madhhab-specific rulings** from classical texts

### Reasoning Process

Every answer follows this fixed process:

1. Check explicit texts (Qur'an / Hadith)
2. Check classical rulings in relevant madhhab(s)
3. Apply usūl al-fiqh principles if no direct ruling exists
4. Use valid qiyās only when conditions are met
5. Mention differences of opinion (ikhtilāf)
6. Declare certainty level
7. State limitations clearly

**If any step fails → the system refuses to issue a ruling.**

---

## Architecture

```
User Question
     ↓
Question Classification
(Fiqh / Aqidah / Hadith / Tafsir / Contemporary)
     ↓
Madhhab Selection
     ↓
Evidence Retrieval
(Qur'an, Hadith, Fiqh, Usūl)
     ↓
Rule-Based Reasoning Pipeline
     ↓
Answer Generation
(Structured, Referenced)
     ↓
Certainty Label + Disclaimer
```

### Key Design Decisions

- **LLM as reasoning engine only**, not knowledge source
- **All knowledge stored externally** in structured databases
- **No memorization** - everything is retrieved
- **Full traceability** from question to source

---

## Data Strategy

All knowledge is stored in **structured, external databases**. No ruling exists without proper documentation.

### Main Data Categories

| Category | Contents |
|----------|----------|
| **Qur'an** | Arabic text + verified translations |
| **Tafsir** | Classical commentaries (Ibn Kathir, Tabari, etc.) |
| **Hadith** | Sahih al-Bukhari, Sahih Muslim, Sunan collections + grading |
| **Fiqh Rulings** | Per-madhhab rulings from classical texts |
| **Usūl al-Fiqh** | Legal maxims and principles |
| **Qawā'id Fiqhiyyah** | Legal maxims (al-Suyuti, Ibn Nujaym, etc.) |
| **Ikhtilāf Metadata** | Documented scholarly differences |
| **Scholar Feedback** | Testing feedback and corrections |

### Required Metadata for Each Ruling

- **Source** (specific text reference)
- **Madhhab** (which school(s) hold this view)
- **Conditions** (when this ruling applies)
- **Certainty Level** (definitive / preponderant / possible / weak)

---

## Madhhab Implementation

### Strategy

- All four Sunni madhhabs supported independently
- No automatic opinion blending
- Ikhtilāf shown clearly and respectfully
- Users can specify madhhab preference

### Implementation Order

1. **Hanafi** (first implementation)
2. **Shafi'i**
3. **Maliki**
4. **Hanbali**

Each madhhab is treated as a separate, complete system with its own:

- Usūl principles
- Qawā'id (legal maxims)
- Source preferences
- Analogy methods

---

## Reasoning Philosophy

The system does **not generate opinions**. It only:

1. **Retrieves** established rulings
2. **Applies** classical usūl principles
3. **Explains** scholarly reasoning
4. **Presents** differences respectfully

### When the System Refuses to Answer

The system will refuse when:

- No clear evidence exists
- Question requires modern ijtihād
- Multiple valid interpretations exist without preponderance
- The question touches on takfīr, politics, or violence
- Insufficient data for confident reasoning

In such cases, the system recommends consulting qualified scholars.

---

## Technical Stack

### Model Choice

- **LLM:** Qwen2.5-3B-Instruct (or equivalent lightweight model)
- **Role:** Reasoning, structuring, and explanation only
- **No initial fine-tuning** (knowledge is retrieved, not learned)

### Why This Model?

- Balanced reasoning ability
- High obedience to structured prompts
- Low operational cost
- Solo-developer friendly
- Easy to control and audit

### Architecture Components

- **Retrieval System:** Vector DB + structured SQL for hadith/fiqh
- **Reasoning Engine:** Rule-based + LLM for explanation
- **Feedback System:** Scholar annotations and corrections
- **Version Control:** All data and reasoning rules are versioned

---

## Scholar Testing & Feedback

### Testing Method

Before any release, multiple senior Islamic scholars will:

1. Interact with the system
2. Evaluate answers using:
   - ✅ **Correct**
   - ❌ **Incorrect**
   - 🟡 **Partially Correct**
   - 🟠 **Partially Incorrect**
   - 🛠 **Correct but Needs Improvement**

3. Provide written feedback for all non-correct responses

### How Feedback is Used

The system **does not auto-update** based on feedback.

Instead, feedback is used to:

- Correct data entries
- Improve reasoning rules
- Add missing conditions
- Refine certainty handling
- Improve linguistic clarity

**High-impact changes require:**

- Multiple scholars agreeing, OR
- Explicit tracking of scholarly disagreement

All changes are **auditable and reversible**.

---

## Safety & Ethics

### The System Will:

✅ Refuse takfīr (declaring others as disbelievers)  
✅ Refuse political rulings  
✅ Refuse calls to violence  
✅ Avoid absolute claims without certainty  
✅ Encourage consulting scholars for complex cases  
✅ Display clear disclaimers on every response  

### Ethical Commitments

- Transparency about limitations
- Scholarly accountability
- Respect for ikhtilāf
- Avoidance of sectarianism
- Accuracy over popularity

---

## Current Status

**Phase:** Data Collection

### Completed

- [ ] Project architecture design
- [ ] Methodology documentation
- [ ] Madhhab strategy
- [ ] Scholar feedback system design

### In Progress

- [x] **Data Collection:**
  - [ ] Qur'an and verified translations
  - [ ] Hadith collections with grading
  - [ ] Fiqh rulings (Hanafi focus first)
  - [ ] Usūl al-Fiqh texts
  - [ ] Tafsir references

### Upcoming

- [ ] Database schema implementation
- [ ] Retrieval system development
- [ ] Reasoning pipeline construction
- [ ] Initial prototype
- [ ] Scholar testing phase
- [ ] Iterative refinement

---

## Roadmap

### Phase 1: Data Foundation (Current)

- Collect and structure Qur'an, Hadith, and Fiqh data
- Build metadata schemas
- Establish data validation processes

### Phase 2: Core System

- Implement retrieval system
- Build reasoning pipeline
- Develop Hanafi madhhab implementation
- Create certainty labeling system

### Phase 3: Scholar Testing

- Recruit scholarly review panel
- Conduct structured testing
- Implement feedback loop
- Iterate based on corrections

### Phase 4: Expansion

- Add remaining madhhabs
- Expand hadith coverage
- Improve reasoning capabilities
- Refine user experience

### Phase 5: Conditional Release

- Obtain scholarly approval
- Public beta (if approved)
- Continuous monitoring
- Ongoing scholarly oversight

**No public release without explicit scholarly approval.**

---

## Contributing

### Current Focus

This is currently a solo development project in the **data collection phase**.

### Future Contributions

Once the foundation is stable, contributions may be welcomed in:

- Data validation
- Source verification
- Testing
- Translations
- Documentation

**All contributions must:**

- Be properly sourced
- Follow scholarly methodology
- Undergo review before integration

---

## Disclaimer

**This system is not a mufti and does not issue fatawa.**

It is a scholarly reasoning assistant designed to:

- Explain classical Islamic methodology
- Present evidence-based reasoning
- Show differences of opinion
- Encourage consultation with qualified scholars

**For religious guidance, consult qualified Islamic scholars in your area.**

The system is designed to support understanding, not replace traditional scholarship.
---

**Built with accountability to Allah ﷻ and respect for classical Islamic scholarship.**
