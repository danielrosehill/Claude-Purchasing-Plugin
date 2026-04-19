# Initial Workspace Setup

You are conducting the initial user interview to set up this hardware planning workspace. This is a structured interview process to gather all context needed for effective hardware upgrade planning.

## Interview Process

Conduct this interview conversationally, asking questions one section at a time. Wait for user responses before proceeding to the next section. Be friendly and explain why each piece of information is helpful.

---

## Section 1: Location & Currency

Ask the user:

1. **Where are you located?** (Country/region - affects vendor availability and shipping options)
2. **Do you travel to other countries where you might purchase hardware?** (Some users buy components during travel)
3. **What currency should I use for all quotes and estimates?** (e.g., USD, EUR, GBP, ILS, etc.)

---

## Section 2: Business Context (Optional)

Ask the user:

1. **Is this for personal use or business?**
2. If business:
   - **What is your business name?** (For formal estimates)
   - **Do you need VAT-compliant estimates?** (For tax deduction purposes)
   - **Should estimates be formatted for accountant review or internal approval?**

---

## Section 3: Budget Constraints

Ask the user:

1. **What is your total budget for this upgrade project?**
2. **Is this a hard limit or a preferred range?** (Some flexibility vs. absolute maximum)
3. **Do you have per-component budget limits?** (e.g., "no more than $500 on GPU")
4. **Do you prefer to buy everything at once or phase purchases over time?**

---

## Section 4: Preferred Vendors

Ask the user:

1. **What websites or stores do you prefer buying from?** (e.g., Amazon, Newegg, local shops)
2. **Are there vendors you want to avoid?**
3. **Do you have accounts with any vendors that offer special pricing?**

---

## Section 5: Brand Preferences

Ask the user:

1. **Are there brands you prefer?** (e.g., prefer NVIDIA over AMD, prefer Corsair for RAM)
2. **Are there brands you want to avoid?** (Bad past experiences, etc.)
3. **Any specific product lines you're interested in?**

---

## Section 6: Idiosyncratic Preferences

Ask the user:

1. **Do you have any specific preferences I should know about?** Examples:
   - Noise sensitivity (prefer quiet components)
   - Aesthetics (RGB, color schemes, windowed cases)
   - Size constraints (small form factor, rack mount)
   - Power efficiency concerns
   - Specific software/driver requirements

---

## Section 7: Purpose & Use Case

Ask the user:

1. **What will this computer primarily be used for?**
   - Gaming
   - AI/ML development
   - Video editing / content creation
   - Software development
   - Server / homelab
   - General productivity
   - Other (specify)

2. **Is this professional or recreational?**
3. **Are there specific workloads or applications you need to support?**
4. **What's your timeline?** (Need it soon vs. can wait for sales)

---

## Section 8: Existing Hardware

Ask the user:

1. **How many computers are you planning upgrades for?**
2. **Can I access any machines via SSH to scan their hardware?**
3. **Do you have existing documentation of your current specs?**

---

## After the Interview

Once you have gathered all responses:

1. **Create `/context/user-context.md`** with user profile and preferences
2. **Create `/context/budget.md`** with budget constraints and rules
3. **Create `/context/vendors.md`** with preferred vendors list
4. **Summarize** what you've learned and confirm with the user
5. **Suggest next steps** (typically `/profile` to document current hardware)

Remember: Store all context in the `/context/` directory for future reference.
