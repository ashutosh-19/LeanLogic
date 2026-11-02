# Prompt For BMad Architecture

Use this prompt to start the `bmad-architecture` skill:

```text
$bmad-architecture

Create the architecture spine for a greenfield wellness-focused fitness nutrition application.

Working mode: Fast path. Draft the first architecture spine with explicit [ASSUMPTION] tags where details are not yet decided. Do not over-design the system; focus on the durable architectural invariants that future product, backend, frontend, and AI-agent work must not diverge on.

Purpose and audience:
The output should help a small product/engineering team align before implementation. The primary deliverable should be an architecture spine. If useful, also identify what should later become PRD/spec inputs, but do not turn this into a full PRD.

Product idea:
Each user gets a personalized team of AI nutrition agents. The app is a wellness app, not a medical or disease-treatment product. The MVP supports only two goals:
1. Fat loss
2. Muscle gain

Both goal flows collect target weight as an input. The architecture should account for target timeframe / desired pace and feasibility checks, because target weight alone can lead to unsafe or unrealistic plans.

Core user inputs:
- Current body weight
- Height
- Goal: fat loss or muscle gain
- Target weight
- Target timeframe or preferred pace
- Age and sex where needed for nutrition calculations
- Activity level and training frequency
- Food allergies and intolerances
- Dietary restrictions and cuisine preferences
- Disliked foods
- Cooking skill, available equipment, and meal prep time
- Budget
- Pantry / already available ingredients, if available
- Adherence feedback, hunger, energy, digestion, substitutions, and missed meals over time

Expected product behavior:
- Generate a weekly diet plan.
- Provide full-day eating plans for each day of the week.
- Include calories and nutritional facts for each meal and item.
- Create recipes for every planned meal.
- Produce daily shopping lists with ingredients and quantities.
- Adapt future plans using the latest user profile, progress, adherence, and feedback data.

Proposed AI agent roles:
- Intake/Profile Agent: collects, updates, and validates user data.
- Goal Interpreter Agent: converts fat loss or muscle gain intent into structured targets and constraints.
- Nutrition Calculation Agent: calculates calorie and macro targets using deterministic nutrition logic where possible.
- Weekly Plan Generator Agent: creates the weekly meal structure and daily plan.
- Recipe Agent: turns every meal into executable recipes with ingredient grams, servings, prep steps, cook time, equipment, substitutions, allergens, leftovers, and item-level nutrition.
- Shopping/Pantry Agent: converts recipes into daily shopping lists, accounts for pantry items, package sizes, reusable ingredients, and waste reduction.
- Adherence/Feedback Agent: captures what the user actually ate, substitutions, skipped meals, hunger, energy, digestion, and progress.
- Safety/Compliance Guard Agent: enforces wellness-only boundaries, unsafe target checks, allergy restrictions, and escalation rules.
- Plan Auditor Agent: checks plans and recipes for calorie/macro alignment, allergens, sodium/fiber/micronutrient concerns, conflicts, and unsafe recommendations.

Key architectural constraints:
- Keep the product in a wellness lane. Avoid disease diagnosis, disease treatment, therapeutic claims, or clinical nutrition workflows.
- Separate deterministic nutrition calculations and safety rules from generative meal/recipe text.
- All agent outputs must be traceable to input data, assumptions, and validation checks.
- The user profile should be modeled as a timeline, not only a mutable current-state record.
- Diet plans and recipes should be versioned so the user can compare, regenerate, or roll back.
- The architecture must support data freshness, confidence, and auditability.
- Privacy, consent, data deletion/export, retention, and health-data handling must be first-class architectural concerns.
- Recipe generation must coordinate with shopping and pantry logic so the app does not create impractical or wasteful plans.
- The plan auditor/safety guard must be able to block, revise, or escalate unsafe outputs before the user sees them.

Architecture questions to resolve:
- What is the recommended high-level architectural paradigm for a multi-agent wellness app: modular monolith first, service-oriented from the start, event-driven workflow, or another approach?
- What are the core bounded contexts/modules?
- What owns mutation of user profile data, goal state, plan state, recipe state, shopping state, and adherence feedback?
- How should AI-agent orchestration work without letting agents create inconsistent hidden state?
- What data should be stored as structured records versus generated text?
- What should be deterministic business logic versus LLM-generated output?
- What invariants are required for safety, auditability, privacy, and plan versioning?
- What should be deferred until after MVP?

Stack:
The stack is open. Recommend a current, well-known starter only if it helps establish coherent defaults. If recommending named technologies, verify current fit before binding them.

MVP boundary:
Include only the architecture needed for fat loss and muscle gain wellness planning, weekly diet plans, per-meal recipes, nutrition facts, shopping lists, profile updates, adherence feedback, safety checks, and plan auditing. Defer athlete-specific, powerlifting-specific, disease-specific, clinician-grade, and marketplace/community features.

Please produce a lean architecture spine with:
- Named architecture paradigm
- Core invariants / architecture decisions with IDs
- Boundary and dependency rules
- State ownership rules
- Agent orchestration rules
- Data model seed at the bounded-context level
- Safety/privacy/audit invariants
- Deferred decisions and open questions
- Minimal diagrams where they clarify structure
```

