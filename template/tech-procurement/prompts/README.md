# User Prompts

Store custom prompts and instructions for the agent here.

## Usage

Create markdown files with specific prompts or instructions you want to reuse:

- `gpu-research.md` - Custom instructions for GPU research
- `budget-constraints.md` - Specific budget rules to apply
- `vendor-priorities.md` - Preferred vendor ordering

## Example Prompt File

```markdown
# GPU Research Parameters

When researching GPUs for my workstation:
- Prioritize ROCm compatibility for AI/ML workloads
- Minimum 12GB VRAM
- Consider power draw (PSU is 750W)
- Prefer quiet cooling solutions
```

The agent will read these files when you reference them during your session.
