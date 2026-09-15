# Tech Ecosystem Growth Analysis: Programming Languages & AI Tooling Adoption

Analysis of how programming language adoption and AI tooling development have shifted on GitHub between Q3 2023 and Q2 2026, using live-pulled API data.

**[View the notebook on Google Colab](https://colab.research.google.com/drive/16_gjuWzS3UN6Fy0Jrsj8ByElhqs0Yhzi?usp=sharing)**

---

## Questions this answers

1. Which programming languages are growing fastest in developer adoption, measured by new repository creation?
2. How fast is AI tooling adoption accelerating — and which category (LLMs, RAG, AI agents, chatbots, generative AI) is leading it?

## Key findings

- **TypeScript grew 447%** in new-repo creation since 2023 — the fastest-growing mainstream language, at more than double JavaScript's rate (+81%).
- **Java and C# stayed nearly flat** (+12% each), consistent with mature enterprise ecosystems rather than new-project growth.
- **AI-agent tooling grew 571x** — from 72 new repos per quarter to over 41,000 — vastly outpacing even the fastest-growing programming language.
- **That growth is still accelerating**, not merely large in aggregate: the most recent two quarters grew roughly 499% over the two quarters before them.

| Language | Growth (2023 Q3 → 2026 Q2) |
|---|---|
| TypeScript | +447% |
| Python | +284% |
| Rust | +234% |
| Go | +139% |
| JavaScript | +81% |
| C++ | +38% |
| Java | +12% |
| C# | +12% |

| AI Topic | Growth Multiple |
|---|---|
| ai-agents | 571x |
| rag | 56x |
| llm | 30x |
| generative-ai | 12x |
| chatbot | 5x |

## Data

Collected directly from the **GitHub Search API** (`api.github.com/search/repositories`), querying repository-creation counts filtered by `language:` and `topic:` across 12 quarters.

- `language_activity_final.csv` — 8 languages × 12 quarters (96 rows)
- `ai_topic_rows.csv` — 5 AI-related topics × 12 quarters (60 rows)
- `ai_tool_snapshot.csv` — supplementary point-in-time snapshot of 8 major AI tool repositories (stars, forks, issues)

## Method

1. **Extraction** — paginated GitHub Search API queries with rate-limit handling, one query per language/topic per quarter
2. **Cleaning** — normalized language identifiers, enforced chronological quarter ordering (alphabetical sorting breaks on `YYYY-Qn` in some contexts), handled failed requests as nulls rather than dropping rows
3. **Analysis** — pandas pivot tables, overall and quarter-over-quarter growth rates, recent-acceleration comparison (last 2 quarters vs. prior 2)
4. **Visualization** — matplotlib with a consistent per-language colour palette, annotated headline figures, and formatted axes

## Limitations

Repository-creation count is a proxy for **developer interest and activity** — it is not a measure of end-user adoption, production usage, or revenue. A repository tagged `llm` may be a serious framework or a weekend experiment; this analysis does not distinguish between them. GitHub topic tags are also self-assigned by repository owners, so topic coverage is inconsistent across projects.

These are standard caveats for developer-ecosystem analytics rather than flaws specific to this dataset, but any conclusion drawn here should be read as directional, not definitive.

## Tools

`Python` · `pandas` · `matplotlib` · `requests` · `GitHub REST API`

## Graphs

<img width="1087" height="587" alt="OP1" src="https://github.com/user-attachments/assets/1f3cb779-ce8d-4692-ac84-8e0a9ce63074" />
<img width="882" height="486" alt="OP2" src="https://github.com/user-attachments/assets/293aad30-f267-40e0-bc68-6c3d7b0c6bdd" />
<img width="1086" height="587" alt="OP3" src="https://github.com/user-attachments/assets/cefcd60f-c3cf-49e7-a056-9a108452ef3b" />
<img width="887" height="486" alt="OP4" src="https://github.com/user-attachments/assets/b4d77b84-db2e-4828-8465-f5e9c9f6bd09" />
<img width="887" height="537" alt="OP5" src="https://github.com/user-attachments/assets/87a6d41e-c382-4a2f-88d6-9e0fa85290bc" />


