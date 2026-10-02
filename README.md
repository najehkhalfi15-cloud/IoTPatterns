# IoT Communication and Security Design Patterns — Replication Package

This repository contains all artifacts for the paper:

> **Modeling of Communication and Security Design Patterns for IoT Applications**

All artifacts are publicly available to support reproducibility and reuse.

---

## Repository Structure

```
iot-patterns-repo/
├── metamodel/
│   └── iot_patterns.ecore          # EMF Ecore metamodel (14 classes, 2 enums)
├── ocl/
│   └── iot_patterns_constraints.ocl # 14 OCL constraints (C1-C3 + Inv1-Inv11)
├── editor/
│   ├── emf/
│   │   └── iot_patterns.genmodel   # EMF GenModel for Java code generation
│   └── gmf/
│       ├── iot_patterns.gmfgraph   # GMF graphical definition (nodes, figures)
│       ├── iot_patterns.gmftool    # GMF palette tools (4 tool groups)
│       └── iot_patterns.gmfmap     # GMF semantic-visual mapping
├── case-studies/
│   ├── smart-irrigation/
│   │   └── SmartIrrigation.xmi     # XMI model instance (8 devices, 5 patterns)
│   └── smart-home/
│       └── SmartHome.xmi           # XMI model instance (6 devices, 5 patterns)
├── simulation/
│   ├── iot_simulation.py           # Behavioral trace generator (5 patterns)
│   └── iot_autoencoder.py          # Autoencoder + baselines (B2-B6)
└── docs/
    └── INSTALL.md                  # Installation guide
```

---

## Metamodel Overview

The Ecore metamodel covers **5 IoT design patterns** in 3 categories:

| Category | Pattern | Key Classes |
|---|---|---|
| Communication | Device Shadow | `VirtualDevice`, `DeviceRegister` |
| Communication | Device Wake-Up Trigger | `WakeUpTrigger`, `IdChannel` |
| Communication | Device Gateway | `Gateway`, `CommunicationLink` |
| Security | Trusted Communication | `SecurityPolicy`, `WhiteList`, `BlackList` |
| Configuration | Remote Bootstrap | `BootstrapServer`, `BootstrapConfig` |

---

## OCL Constraints (14 total)

### Composition Constraints
| ID | Name | Rule |
|---|---|---|
| C1 | `TrustedCommRequired` | Active links require both endpoints whitelisted |
| C2 | `UnconfiguredImpliesBlacklisted` | Unconfigured device → blacklist |
| C3 | `ConfiguredImpliesWhitelisted` | Configured device → whitelist |

### Pattern Invariants
| ID | Pattern | Name |
|---|---|---|
| Inv1 | Device Shadow | `UniqueShadowAssociation` |
| Inv2 | Device Shadow | `ShadowConsistency` |
| Inv3 | Device Shadow | `ConnectivityRequired` |
| Inv4 | Device Gateway | `MustUseGateway` |
| Inv5 | Wake-Up Trigger | `NoCommunicationDuringSleep` |
| Inv6 | Wake-Up Trigger | `ValidWakeUpTransition` |
| Inv7 | Trusted Communication | `TrustedOnly` |
| Inv8 | Trusted Communication | `WhiteListRequired` |
| Inv9 | Trusted Communication | `MutualAuthRequired` |
| Inv10 | Remote Bootstrap | `HasBootstrapConfig` |
| Inv11 | Global | `SecureAndAvailableCommunication` |

---

## Eclipse Editor Setup

### Requirements
- Eclipse Modeling Tools 2023-09 or later
- EMF (Eclipse Modeling Framework) — included
- GMF (Graphical Modeling Framework) Runtime 1.9+
- OCLinEcore or Eclipse OCL plugin

### Installation Steps
1. Clone this repository
2. Open Eclipse → **File > Import > Existing Projects into Workspace**
3. Import the `metamodel/` folder as an EMF project
4. Open `iot_patterns.ecore` → right-click → **Generate Model Code**
5. Import the `editor/emf/iot_patterns.genmodel` → right-click → **Generate Edit Code** and **Generate Editor Code**
6. Open `editor/gmf/iot_patterns.gmfmap` → **Derive GMFGen model** → **Generate diagram code**
7. Run as Eclipse Application → the graphical editor opens

### Palette Groups
The editor palette contains 4 tool groups:
- **Communication Pattern Tools**: IoT System, Device, Sensor, Actuator, Server, Gateway, Device Shadow, Wake-Up Trigger
- **Security Pattern Tools**: Security Policy, WhiteList, BlackList, Trusted Endpoint
- **Bootstrap Pattern Tools**: Bootstrap Server, Bootstrap Config
- **Connection Tools**: Communication Link, Connector

---

## Case Studies

### Smart Irrigation System
- **File**: `case-studies/smart-irrigation/SmartIrrigation.xmi`
- **Devices**: 4 soil moisture sensors (ZigBee, sleep mode) + 4 electrovalves (IP)
- **Gateway**: ZigBee→IP protocol translation
- **Violations detected (initial model)**: 19
- **Violations after correction**: 0 / all 14 OCL constraints satisfied

### Smart Home System
- **File**: `case-studies/smart-home/SmartHome.xmi`
- **Devices**: 3 temperature sensors (ZigBee) + 2 smart lights + 1 door lock (WiFi/IP)
- **Gateway**: ZigBee→WiFi protocol translation
- **Violations detected (initial model)**: 15
- **Violations after correction**: 0 / all 14 OCL constraints satisfied

---

## Citation

If you use these artifacts, please cite:

```bibtex
@inproceedings{anonymous2026iotpatterns,
  title     = {Modeling of Communication and Security Design Patterns for IoT Applications},
  author    = {Anonymous},
  booktitle = {Proceedings of [Conference Name]},
  year      = {2026}
}
```

---

## License

MIT License — see `LICENSE` file.
