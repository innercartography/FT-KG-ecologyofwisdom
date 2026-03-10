# Frontier Tower — Knowledge Graph Concept

**An independent exploration of what a knowledge graph could look like at a 16-floor vertical village in San Francisco.**

> **Provenance:** This project was conceived and built independently by a member of Frontier Tower. It does not represent the organization, its founders, or any official initiative. No commitments have been made by or on behalf of Frontier Tower. This is a personal contribution to a conversation that may already be happening through other channels — offered in that spirit.

---

## The Problem It Solves

Frontier Tower already has community infrastructure — a Telegram group with both a public-facing and citizens-only channel, members like Sameer running their own knowledge graphs with their own ontologies, floor-level communities organizing events, priorities, and projects in their own ways.

The problem isn't lack of activity. It's lack of cohesion across it. Apps, approaches, events, and priorities accumulate in parallel without a connective layer. Knowledge generated at a hackathon on F2 doesn't reach the longevity researchers on F11. A founder on F10 doesn't know a team on F9 is building exactly the infrastructure they need. The Telegram channels capture presence but not meaning.

The hypothesis here — informed by seeing Bonfires in action at ethBoulder — is that the **episodic, event-anchored approach** Bonfires takes is particularly well-suited to surfacing this latent knowledge base. Multi-community environments with high activity and low coordination aren't missing data. They're missing a way to make the data legible across different ontologies at the right moment. Bonfires did that at ethBoulder. Frontier Tower is a more permanent, more densely connected version of the same problem.

The schema and prototype in this repo are an attempt to sketch what that looks like for this specific building — not as a top-down taxonomy, but as a substrate that respects how knowledge actually accumulates here: floor by floor, event by event, person by person.

---

## What's in This Repo

```
/
├── frontier-tower-hyperblog.html   # Self-contained interactive prototype
├── schema/
│   └── world.json                  # Entity + relationship schema (draft)
├── floors/
│   └── (per-floor pages, forthcoming)
└── README.md
```

The hyperblog requires no build step and no backend. It runs from a single file.

---

## The 16 Floors

| Floor | Name | Domain |
|-------|------|--------|
| 16 | d/acc Lounge | Cross-pollination & community |
| 15 | Coworking & The Library | Deep work & focus |
| 14 | Human Flourishing | Sense-making, coordination, regeneration |
| 12 | Ethereum & Decentralized Tech | DeFi, L2, RWA, Web3 |
| 11 | Longevity and Health | Aging research, biotech, biomarkers |
| 10 | Frontier @ Accelerate | Founders, VCs, venture ecosystems |
| 9 | AI and Autonomous Systems | Multi-agent AI, hardware, autonomy |
| 8 | Neuro and Biotech | Gene editing, synthetic biology, BSL-2 lab |
| 7 | Frontier Makerspace | Hardware, CNC, 3D printing, electronics |
| 6 | Art and Music | Generative art, installations, creative tech |
| 5 | Movement & Fitness Center | Gym, yoga, sauna, cold plunge |
| 4 | Robotics & Hard Tech | Robotics, advanced materials, deep tech |
| 3 | Private Offices | Startup teams up to 20 |
| 2 | Event & Hackathon Space | Events, workshops, hackathons |
| 1 | Ground Floor — Entrance | Orientation, commons, first contact |

*(No Floor 13)*

---

## Graph Schema — Entity Types

| Entity | Key Fields |
|--------|-----------|
| `Person` | name, role, floor(s), interests, visibility |
| `Floor` | number, name, focus, shard_policy, open_questions |
| `Project` | title, status, participants, themes, needs, offers |
| `Event` | name, date, location, hosts, themes, outcomes |
| `Theme` | label, floors, related_themes, translation_cost |
| `Shard` | owner, scope, visibility, published_nodes, policies |
| `Daemon` | function, scope, input_modes, output_types |
| `Bridge` | source_floor, target_floor, shared_themes, translation_cost, status |

### Key Relationships

```
Person   → belongs_to     → Floor
Person   → working_on     → Project
Project  → needs/offers   → Theme
Floor    → publishes_to   → SharedGraph
Floor    → bridges_to     → Floor  (via Bridge node)
Event    → generates      → Quest
Bridge   → translated_by  → Daemon
Theme    → contested_by   → Theme  (cross-floor tension)
```

---

## Visibility Model

Nothing meaningful is exposed by default. Each shard controls its own disclosure.

```
Private
  └─ Trusted small group
      └─ Floor-internal
          └─ Cross-floor (opt-in)
              └─ Building-wide public
                  └─ Machine-readable / API
```

---

## Cross-Floor Bridges — Natural Adjacencies

| Bridge | Shared Themes | Translation Cost |
|--------|--------------|------------------|
| F9 ↔ F14 | AI as collective intelligence; care coordination | Moderate |
| F8 ↔ F11 | Biomarkers, personalized medicine, aging | Low |
| F12 ↔ F10 | Governance, capital formation, on-chain coordination | Low |
| F9 ↔ F8 | Neuro-AI convergence, brain-computer interfaces | Moderate |
| F7 ↔ F4 | Hardware fabrication, physical-digital synthesis | Low |

---

## Deploying the Hyperblog

```bash
# GitHub Pages — push repo, enable Pages, point to root
# Vercel — vercel deploy frontier-tower-hyperblog.html
# Anything static — copy the file, done
```

---

## For the Bonfires Team

If you're already in conversations with Frontier Tower through other channels — great. This work is compatible with that, not competing with it. The schema, floor map, and prototype are freely available to inform whatever you're building.

I attended ethBoulder and watched Bonfires surface connections across a multi-community event that wouldn't have happened otherwise. Frontier Tower is a more permanent, more densely layered version of that same context — 16 communities, a coliving component, recurring events, and existing knowledge infrastructure that isn't yet talking to itself. The episodic approach seems like exactly the right entry point.

The practical questions worth exploring: how Bonfires handles layered shard visibility across communities, whether it can work alongside existing tools (Telegram, individual knowledge graphs), and what the event-anchored onboarding path looks like for a standing community rather than a conference.

Happy to discuss any of it.

---

*Independent work by a Frontier Tower member · Not an official Frontier Tower project*
