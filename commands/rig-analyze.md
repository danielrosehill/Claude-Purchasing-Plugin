# Hardware Analysis

You are analyzing the user's hardware configuration to identify bottlenecks, compatibility issues, and upgrade opportunities.

## Prerequisites

Check that hardware profiles exist in `/context/machines/`. If not, suggest running `/profile` first.

## Analysis Process

### 1. Load Context

Read:
- `/context/user-context.md` - User preferences and use case
- `/context/budget.md` - Budget constraints
- `/context/machines/{name}/` - Hardware specifications

### 2. Compatibility Analysis

Check for:

**CPU & Motherboard**
- Socket compatibility
- Chipset support for CPU features
- BIOS update requirements for newer CPUs
- VRM adequacy for power-hungry CPUs

**Memory**
- DDR generation compatibility
- Speed support by motherboard/CPU
- Channel configuration (single vs dual vs quad)
- Maximum supported capacity

**GPU**
- PCIe slot availability and generation
- Physical clearance in case
- Power connector requirements
- PSU wattage headroom

**Storage**
- Available SATA ports
- M.2 slots (and their PCIe lane allocation)
- NVMe support

**Power**
- Total system power draw estimate
- PSU headroom for upgrades
- Required power connectors

### 3. Bottleneck Analysis

Identify performance bottlenecks based on user's use case:

**For Gaming:**
- CPU single-thread performance vs GPU tier
- RAM speed and capacity
- Storage speed for load times

**For AI/ML:**
- GPU VRAM capacity
- System RAM for model loading
- CPU for data preprocessing
- Storage for datasets

**For Content Creation:**
- CPU multi-thread performance
- GPU acceleration support
- RAM capacity
- Fast storage for scratch disks

**For Development:**
- RAM capacity
- Storage speed (especially for IDEs, VMs)
- CPU multi-thread for compilation

### 4. Upgrade Path Analysis

Identify realistic upgrade options:

**Quick Wins** (minimal effort, good impact)
- RAM upgrades within existing platform
- Storage additions
- Cooling improvements

**Major Upgrades** (moderate investment)
- GPU upgrade
- CPU upgrade (same socket)
- PSU upgrade

**Platform Changes** (significant investment)
- New motherboard + CPU + RAM
- Full system replacement

---

## Output

Save analysis to `/outputs/analysis/YYYY-MM-DD_{machine-name}_analysis.md`:

```markdown
# Hardware Analysis: {Machine Name}

**Analysis Date:** YYYY-MM-DD
**Use Case:** {from user context}

## Current Configuration Summary
[Brief overview of specs]

## Compatibility Status
[Any issues or limitations identified]

## Bottleneck Analysis
[Based on use case, what's limiting performance]

## Upgrade Opportunities

### Quick Wins
- [List with expected impact]

### Recommended Upgrades
- [Prioritized list based on use case and budget]

### Future Considerations
- [Platform limitations to be aware of]

## Budget Alignment
[How recommendations fit within stated budget]
```

---

## After Analysis

Offer to:
- Run `/recommend` for specific component recommendations
- Run `/estimate` to price out suggested upgrades
- Run `/compare` to evaluate specific component options
