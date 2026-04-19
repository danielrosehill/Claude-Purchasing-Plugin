# Hardware Profile Scan

You are documenting the hardware specifications for a machine. This profile will be used for compatibility analysis and upgrade recommendations.

## Process

1. **Identify the machine** - Ask the user which machine to profile and what to call it (e.g., "workstation", "gaming-pc", "server-01")

2. **Determine access method:**
   - **Local machine**: Can run commands directly
   - **SSH access**: Connect via SSH to scan remotely
   - **Manual input**: User will provide specs manually
   - **Import from file**: User has system info export in `/inputs/`

3. **Gather specifications** using appropriate method

---

## For Local or SSH Access

Run hardware detection commands to gather:

### CPU
```bash
lscpu | grep -E "Model name|Architecture|CPU\(s\)|Thread|Core|Socket|MHz"
cat /proc/cpuinfo | grep -E "model name|cpu cores" | head -4
```

### Memory
```bash
free -h
sudo dmidecode -t memory | grep -E "Size|Type|Speed|Manufacturer"
```

### GPU
```bash
lspci | grep -E "VGA|3D"
# For NVIDIA:
nvidia-smi --query-gpu=name,memory.total,driver_version --format=csv 2>/dev/null
# For AMD:
rocm-smi --showproductname 2>/dev/null
```

### Storage
```bash
lsblk -o NAME,SIZE,TYPE,MODEL
df -h
```

### Motherboard
```bash
sudo dmidecode -t baseboard | grep -E "Manufacturer|Product|Version"
```

### Power Supply
Ask user - cannot be detected programmatically

### Case
Ask user - cannot be detected programmatically

---

## Output Structure

Create the following files in `/context/machines/{machine-name}/`:

### 1. `{machine-name}_spec.json`
Machine-readable complete specification:
```json
{
  "profile_date": "YYYY-MM-DD",
  "machine_name": "...",
  "cpu": { ... },
  "memory": { ... },
  "gpu": { ... },
  "storage": [ ... ],
  "motherboard": { ... },
  "psu": { ... },
  "case": { ... }
}
```

### 2. `{machine-name}_summary.md`
Human-readable summary with brief analysis:
- Overview of the build
- Notable strengths
- Potential bottlenecks
- Upgrade-relevant notes (available slots, expansion options)

### 3. Component-specific files (optional)
For detailed component analysis:
- `cpu.md`
- `gpu.md`
- `memory.md`
- `storage.md`

---

## Important Notes

- **Always verify the current date** using TIME MCP or asking the user
- **Record the profile date** on all output files
- **Ask about PSU wattage and efficiency rating** - critical for upgrade planning
- **Note available expansion slots**: PCIe slots, RAM slots, drive bays
- **Check for warranty information** if available
- **Offer to redact serial numbers** if user plans to share publicly

---

## After Profiling

Summarize what you found and suggest:
- Run `/analyze` to check for bottlenecks
- Run `/recommend` if user has specific upgrade goals
- Profile additional machines if planning multiple upgrades
