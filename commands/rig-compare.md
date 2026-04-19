# Component Comparison

You are helping the user compare specific components to make an informed purchasing decision.

## Usage

User may specify components to compare, or ask for comparison within a category (e.g., "compare RTX 4070 vs RX 7800 XT" or "compare mid-range GPUs for my use case").

## Process

### 1. Identify Components

If user hasn't specified:
- Ask what component type to compare
- Suggest relevant options based on their use case and budget
- Offer 2-4 options for comparison

### 2. Gather Specifications

For each component, compile:

**General**
- Full product name
- Current price (user's currency, from preferred vendors)
- Release date
- Warranty

**Performance**
- Benchmark scores relevant to use case
- Real-world performance examples
- Comparison to user's current hardware

**Technical Specs**
- Component-specific specifications (see below)

**Practical Considerations**
- Power requirements
- Cooling requirements
- Physical dimensions
- Compatibility with user's system

---

## Component-Specific Data Points

### GPUs
- VRAM (amount, type, bandwidth)
- CUDA cores / Stream processors
- Base/Boost clocks
- TDP
- Power connectors required
- Length (for case clearance)
- Benchmark scores (gaming, compute, AI/ML)

### CPUs
- Cores / Threads
- Base/Boost clocks
- Cache sizes
- TDP
- Socket
- Integrated graphics
- Benchmark scores (single-thread, multi-thread)

### RAM
- Capacity
- Speed (MT/s)
- Latency (CL)
- Voltage
- Heat spreader
- XMP/EXPO profiles

### Storage
- Capacity
- Interface (SATA, NVMe Gen3/4/5)
- Sequential read/write speeds
- Random IOPS
- Endurance (TBW)
- Cache type

### Power Supplies
- Wattage
- Efficiency rating (80+ tier)
- Modular type
- Rail configuration
- Connector availability
- Fan noise

---

## Output Format

Save to `/outputs/analysis/YYYY-MM-DD_{component-type}_comparison.md`:

```markdown
# {Component Type} Comparison

**Date:** YYYY-MM-DD
**Use Case:** {user's use case}
**Budget:** {user's budget}

## Candidates

| | Option A | Option B | Option C |
|---|----------|----------|----------|
| **Model** | Product X | Product Y | Product Z |
| **Price** | $XXX | $XXX | $XXX |
| **Spec 1** | value | value | value |
| **Spec 2** | value | value | value |

## Performance Comparison

### For {Use Case}
[Benchmark data and analysis]

### Real-World Impact
[What the user will actually notice]

## Pros & Cons

### Option A: {Product Name}
**Pros:**
- ...

**Cons:**
- ...

**Best for:** {who should buy this}

[Repeat for each option]

## Recommendation

Based on your {use case} and {budget}, I recommend **{Product}** because:
1. {Reason}
2. {Reason}

### If budget allows...
Consider {alternative} for {benefit}

### If budget is tight...
{Option} offers {value proposition}

## Compatibility Check
[Confirmation that recommendation works with user's system]
```

---

## Tips

- **Always check compatibility** with user's existing system
- **Consider total cost** (may need new PSU, cables, etc.)
- **Note regional availability** - some products harder to find in certain regions
- **Check reviews** for real-world reliability data
- **Consider future upgradeability** when relevant
