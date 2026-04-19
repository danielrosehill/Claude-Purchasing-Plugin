# Agent Outputs

This is the AI agent's working directory. All analysis, recommendations, estimates, and generated documents will be saved here.

## Structure

The agent will organize outputs into subdirectories as needed:

- **`/analysis/`** - Hardware compatibility analysis, benchmark comparisons
- **`/estimates/`** - Cost estimates and quotes (formatted for approval/VAT purposes)
- **`/recommendations/`** - Component recommendations and upgrade paths
- **`/reports/`** - Summary reports and planning documents

## File Naming Convention

Files are named with ISO date prefix for easy sorting:
- `YYYY-MM-DD_description.md`
- Example: `2024-12-14_gpu-upgrade-analysis.md`

## Note

This directory is the agent's workspace. Users should review outputs here but avoid modifying files directly—request changes through the agent instead.
