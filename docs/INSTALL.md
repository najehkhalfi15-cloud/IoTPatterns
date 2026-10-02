# Installation Guide — IoT Patterns Eclipse Editor

## Prerequisites

| Tool | Version | Download |
|---|---|---|
| Eclipse Modeling Tools | 2023-09+ | https://www.eclipse.org/downloads/packages/ |
| Java JDK | 17+ | https://adoptium.net |
| GMF Runtime | 1.9+ | Eclipse Marketplace |
| Eclipse OCL | 6.20+ | Eclipse Marketplace |

## Step-by-Step Setup

### 1. Install Eclipse plugins
In Eclipse: **Help → Eclipse Marketplace**
- Search "GMF Runtime" → Install
- Search "Eclipse OCL" → Install
- Restart Eclipse

### 2. Import the metamodel project
```
File → Import → General → Existing Projects into Workspace
→ Select: metamodel/
```

### 3. Generate domain model code
```
Open: iot_patterns.ecore
Right-click → New → Other → EMF Generator Model
→ Select iot_patterns.genmodel
Right-click genmodel → Generate Model Code
                     → Generate Edit Code
                     → Generate Editor Code
```

### 4. Generate the graphical editor
```
Open: editor/gmf/iot_patterns.gmfmap
Right-click → Derive GMFGen model
Right-click gmfgen → Generate diagram code
```

### 5. Launch the editor
```
Right-click on any generated plugin project
→ Run As → Eclipse Application
→ File → New → Other → IoT Patterns Diagram
```

### 6. Validate OCL constraints
```
Install: Eclipse OCL plugin (Step 1)
Open your .xmi model instance
Right-click → Validate
→ All 14 OCL constraints are checked automatically
```

## Troubleshooting

| Problem | Solution |
|---|---|
| "Plugin not found" | Ensure all 3 plugin projects are in the workspace |
| OCL validation fails to load | Verify Eclipse OCL plugin is installed |
| Empty palette | Re-derive GMFGen from gmfmap and regenerate |
