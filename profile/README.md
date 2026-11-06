# EYEAR

**Eyes and Ears for Proactive Smart Home Orchestration through Spatial Awareness and Multi-Agent Collaboration**

Hanyang University | Fall 2026 | CSE406 Software Engineering + ITE351 AI & Applications

EYEAR investigates how room-level sensing can support proactive, explainable coordination of smart-home appliances. Local camera, microphone, and mmWave processing produces semantic observations. A whole-home World Model combines them, four role-based agents advise a central Home Orchestrator, and validated commands operate virtual appliances.

> Independent academic prototype. EYEAR is not an official LG Electronics product. The course prototype does not modify ThinQ ON firmware, integrate with the production ThinQ application, or control physical LG appliances.

## Representative demonstration

A resident enters a bedroom and lies down. The vacuum defers that room, a neighboring washer switches to low-noise mode, and the central service asks whether the resident is going to sleep. An affirmative answer closes the curtain and turns off the light; a negative answer or no reply leaves them unchanged. Radar supports continued occupancy observation in the dark. A later direct voice command turns the light on, and the deferred cleaning task becomes eligible after the room is vacated.

The demonstration also shows shared-room temperature preferences: residents preferring 24 and 26 degrees Celsius lead to a proposed 25-degree target, with airflow toward the resident preferring cooler air. These are project policies for simulated devices, not claims about physical appliance capabilities.

## System overview

```text
Local Node: camera + microphone + speaker + mmWave
  -> semantic events (no raw camera/audio in central messages)
  -> World Model / whole-home snapshot
  -> Cleaning | Noise | Temperature | Lighting agents
  -> Home Orchestrator: arbitration + dialogue + policy validation
  -> virtual appliances -> execution feedback -> World Model

Next.js UI <-> Spring Boot application backend <-> Orchestrator
Orchestrator <-> Node: spoken text, replies, and direct commands
```

## Current scope and status

- Primary scenario: bright-room entry, resting, voice confirmation, dark-room occupancy, direct command, and deferred-task resumption.
- One physical surrogate Node; other rooms are represented by simulated event publishers.
- Four-agent architecture is the current scenario baseline. Learned agent scorers remain optional research candidates.
- Components are being developed independently. Integrated execution and measured evaluation results are not claimed here.
- A controlled fallback path is planned for LLM unavailability. Any offline or replay mode must be labeled in the interface.

## Repositories

| Repository | Owner | Responsibility |
| --- | --- | --- |
| [.github](https://github.com/HY-LG-EYEAR/.github) | Shared | Organization profile and repository navigation |
| [LG-EYEAR](https://github.com/HY-LG-EYEAR/LG-EYEAR) | Shared | Integration, shared contracts, scenario fixtures, and reproducible demo configuration |
| [eyear-node](https://github.com/HY-LG-EYEAR/eyear-node) | Banseok Shin | Local perception, sensor fusion, speech input/output, and semantic event publishing |
| [eyear-worldmodel](https://github.com/HY-LG-EYEAR/eyear-worldmodel) | Hyochang Lee | Whole-home state fusion, virtual appliances, and home simulation |
| [eyear-orchestrator](https://github.com/HY-LG-EYEAR/eyear-orchestrator) | Jungbin Song | Four agents, central arbitration, policy validation, dialogue, and agent experiments |
| [eyear-app](https://github.com/HY-LG-EYEAR/eyear-app) | Yewon Joung | Next.js frontend and Spring Boot application backend |
| [LG-EYEAR-docs](https://github.com/HY-LG-EYEAR/LG-EYEAR-docs) | Shared | CSE406 IEEE LaTeX sources and software engineering deliverables |
| [LG-EYEAR-blog](https://github.com/HY-LG-EYEAR/LG-EYEAR-blog) | Shared | ITE351 datasets, methodology, evaluation, and technical blog |

## Team

| Member | Affiliation | Responsibility | Email |
| --- | --- | --- | --- |
| Jungbin Song | Dept. Information Systems, Hanyang University | AI Agent & Control Systems Engineer; Customer | happysongjb@hanyang.ac.kr |
| Banseok Shin | Dept. Information Systems, Hanyang University | Edge AI & Sensor Systems Engineer | sbs000126@hanyang.ac.kr |
| Hyochang Lee | Dept. Information Systems, Hanyang University | Data Fusion & Simulation Engineer | hyo8993@hanyang.ac.kr |
| Yewon Joung | Dept. Information Systems, Hanyang University | Full-Stack Software Engineer; User | jyw0495@hanyang.ac.kr |

## Reports and demonstration

- [CSE406 engineering documents](https://github.com/HY-LG-EYEAR/LG-EYEAR-docs)
- [ITE351 technical blog](https://github.com/HY-LG-EYEAR/LG-EYEAR-blog)
- [System integration and reproduction guide](https://github.com/HY-LG-EYEAR/LG-EYEAR)
- Demo recording: pending publication.
- Measured results: pending evaluation.

Course deadlines and submission checklists are maintained in the two course repositories. The integration repository records compatible component and contract versions.
