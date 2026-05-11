# hmz-paperclip-trends-scanner

> **Autonomous market trends scanner | Mon/Wed/Fri 6:00 AM | keeps DigiMinds ahead of the market**

[![schedule](https://img.shields.io/badge/schedule-Mon_Wed_Fri_6AM-blue?style=flat)](.) [![trends](https://img.shields.io/badge/output-market_signals-purple?style=flat)](.) [![status](https://img.shields.io/badge/status-always_on-brightgreen?style=flat)](.) [![company](https://img.shields.io/badge/company-DigiMinds-orange?style=flat)](.)

[Overview](#overview) · [Sources](#sources) · [Signal Types](#signal-types) · [Output](#output) · [Tips](#tips)

---

## 🧠 OVERVIEW

Paperclip Trends Scanner fires three times a week (Mon/Wed/Fri at 6 AM) to scan macro market trends, platform algorithm changes, emerging ad formats, and economic signals affecting the PPC industry. Findings feed into the CEO loop and weekly strategy context.

| Component | Value |
|---|---|
| Trigger | Mon/Wed/Fri 6:00 AM (LaunchAgent) |
| Scope | Google Ads, Meta Ads, PPC industry, macro economy |
| Output | Trends brief → Paperclip API → CEO loop |
| Model | Gemini 2.0 Flash + Groq (zero Claude tokens) |

---

## 🎯 SIGNAL TYPES TRACKED

| Signal Category | Examples | Source |
|---|---|---|
| Platform changes | Google Ads new features, Meta algorithm shift | Official blogs + Apify |
| Industry trends | AI in PPC, automation wave, attribution changes | Google News |
| Economic signals | Consumer spending, CPM/CPC macro trends | Industry reports |
| Emerging formats | New ad format launches, placements | Platform blogs |
| Regulatory | Privacy law changes affecting targeting | News API |
| Competitor positioning | Industry shifting to Performance Max? | LinkedIn + intel |

---

## ⚙️ PIPELINE

```
Mon/Wed/Fri 6:00 AM
    │
    ├─► Fetch Google Ads blog + announcements (Apify)
    ├─► Fetch Meta Business blog + Reels ads news (Apify)
    ├─► Google News: "PPC 2025", "Google Ads update", "Meta ads"
    ├─► Industry: Search Engine Land, Marketing Land RSS
    │
    ├─► Gemini Flash: summarize + extract actionable signals
    ├─► Rank by impact score (High/Medium/Low for DigiMinds)
    │
    └─► POST /api/trends → stored + injected into next CEO loop
```

---

## 💡 TIPS

■ **Signal Quality (4)**
| Tip | Source |
|---|---|
| Platform official blogs are ground truth — weight 3x over news articles | Intel SOP |
| "Emerging" trends need 2+ sources before flagging as HIGH impact | Validation rule |
| Mon scan is most important — covers weekend announcements | Schedule logic |
| Economic signals (CPI, consumer confidence) affect client ad budgets | Strategy context |

■ **Operations (3)**
| Tip | Source |
|---|---|
| Latest trends at `/api/trends/latest` — always 3 days fresh | API ref |
| CEO loop ingests trends automatically every 6h | CEO loop integration |
| Manual scan: `~/.claude/bin/paperclip-trends-scanner` | CLI ref |

---

## ☠️ TOOLS REPLACED

| Trends Scanner | Replaced |
|---|---|
| Market trend awareness | Occasional Twitter/LinkedIn browsing |
| Platform update tracking | Missing Google Ads changes until client impacted |
| Macro signal detection | Ignoring economic context entirely |
| Strategic context for CEO | Flying blind on market shifts |

---

*Part of [DigiMinds AI Agency Stack](https://github.com/hmzainjamil) — Paperclip autonomous trends intelligence*
