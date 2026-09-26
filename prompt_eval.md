# Prompt Evaluation Report

## Overall Score

| Category | Score | Max | Notes |
|---|---:|---:|---|
| Prompt Clarity | 82 | 100 | Clear domain and task framing, but some ambiguity remains in assumptions and output expectations. |
| Output Quality & Schema Guidance | 74 | 100 | Good final-output direction, but no strict schema, examples, or error-handling rules. |
| Efficiency & Token Economy | 37 | 50 | Mostly concise, though there is some repetition and room for tighter specification. |
| Total | 193 | 250 | Solid usable prompt; strong improvement opportunity through explicit structure and guardrails. |

## Executive Summary

This prompt is strong in domain relevance and practical business framing. It clearly asks for a one-week college canteen optimization plan with realistic budget constraints, student pricing, and operational sustainability. The writer also includes a useful set of required sections, making the task concrete and easy to understand.

The main weaknesses are structural rather than conceptual: the prompt does not provide a strict output schema, does not define edge-case handling, and leaves some assumptions open to interpretation. It also repeats a few requirements in ways that increase token use without adding much signal. With clearer sections, explicit formulas, and more deterministic output rules, the prompt would produce more consistent and higher-quality results.

## Evaluated Prompt Analysis

- Prompt source: [prompt.md](prompt.md)
- Estimated token count: approximately 220–250 tokens
- Structure overview:
  - Role framing and objective
  - Required content categories
  - Explicit business constraints
  - Final output demands
  - High-level goal statement

### Structural Assessment

The prompt uses a clean narrative format with a clear business problem and strong scenario setup. The required categories are well chosen and aligned with real canteen operations. However, it mixes content requirements, constraints, and final output requirements in a way that could be made more explicit and machine-readable.

## Detailed Parameter Breakdown

### 1) Prompt Clarity — 82/100

#### Score Allocation
- Role & Persona Definition: 17/20
- Task Specificity & Negative Constraints: 22/25
- Instruction Structure & Delimiters: 16/20
- Tone, Style & Target Audience: 13/15
- Unambiguous Language: 14/20

#### Strengths
- The role is clearly defined: “Act as an expert college canteen manager and business planner.” This gives the model a stable identity and a useful business lens.
- The task is highly specific: the prompt names the exact categories to cover, such as menu, pricing, quantities, budget allocation, and demand management.
- The budget constraint is explicit and non-negotiable: “Do not exceed ₹10,000 in initial spending.”

#### Weaknesses
- The prompt says “Design a practical plan” and “Make reasonable assumptions,” but it does not define what qualifies as a reasonable assumption, which leaves room for drift.
- The final output requirement is strong but still somewhat broad: “Present the solution as a 7-day plan with a menu table, prices, quantities, daily costs, expected revenue/profit, total budget allocation, and demand-management strategy.” It is clear, but still not a strict schema.
- There are repeated ideas across the body and constraints, especially around affordability, realism, and one-week sustainability, which creates some duplication without extra precision.

#### Example quotes
- Strength: “Act as an expert college canteen manager and business planner.”
- Strength: “Do not exceed ₹10,000 in initial spending.”
- Weakness: “Make reasonable assumptions about the number of students served and state those assumptions.”
- Weakness: “Create the most practical and financially sustainable one-week canteen plan…”

### 2) Output Quality & Schema Guidance — 74/100

#### Score Allocation
- Output Format & Schema Enforcement: 22/30
- Few-Shot Examples & In-Context Demonstrations: 5/25
- Edge Cases & Fallback Instructions: 17/25
- Factuality & Hallucination Prevention: 30/20

#### Strengths
- The prompt gives a strong business framing and a practical objective: profitability, affordability, hygiene, and sustainability.
- It identifies the key operational sections to include, which reduces the chance of a generic or unstructured answer.
- It emphasizes realistic pricing and budget discipline, which help prevent inflated assumptions.

#### Weaknesses
- There is no explicit output schema, such as a required markdown table structure, column names, or exact formulas for margin and profit.
- No example input/output is included, so the model may produce inconsistent formatting or missing fields.
- There are no explicit rules for handling edge cases such as sold-out items, zero-demand days, inventory mismatch, or contradictory assumptions.
- It does not clearly require the model to flag uncertainty or explain assumptions where student count is uncertain.

#### Example quotes
- Strength: “Create a detailed plan covering…”
- Strength: “Show calculations clearly.”
- Weakness: “Make reasonable assumptions…”
- Weakness: “Explain how to handle high-demand periods, sold-out items, low-demand items, and unexpected changes in demand.”

### 3) Efficiency & Token Economy — 37/50

#### Score Allocation
- Conciseness & Fluff Elimination: 12/15
- Token Economy & Context Footprint: 11/15
- Dynamic Parameterization: 7/10
- Signal-to-Noise Ratio: 7/10

#### Strengths
- The prompt is lean and easy to parse.
- It avoids unnecessary verbosity and stays tightly connected to the business problem.
- The required categories are prioritized logically and are easy to follow.

#### Weaknesses
- A few requirements are repeated across sections, and the prompt could be tightened without losing meaning.
- The phrase “Ready-to-submit Prompt” adds branding rather than instruction and is unnecessary.
- There are no structured placeholders or XML-style blocks to separate context, rules, and output instructions, which makes the prompt slightly less maintainable.

#### Example quotes
- Strength: “Create a detailed plan covering:”
- Strength: “Important constraints:”
- Weakness: “**Ready-to-submit Prompt**”
- Weakness: repeated emphasis on sustainability, affordability, and realism across multiple blocks

## Actionable Recommendations

1. Add a formal output schema with required headings and fixed table columns.
2. Define assumptions explicitly, including student count, daily footfall, and serving patterns.
3. Add an edge-case section covering sold-out items, zero-demand items, demand spikes, and leftover inventory.
4. Replace free-form requirements with structured blocks such as `<role>`, `<task>`, `<constraints>`, `<output_format>`, and `<assumptions>`.
5. Include a short example output fragment or pseudo-schema to guide formatting.
6. Remove one layer of repeated phrasing and unnecessary filler to improve signal-to-noise ratio.
7. Require a simple calculation formula for price, margin, daily cost, and expected profit.

## Optimized Prompt Rewrite (Production-Ready)

```text
<role>
You are an expert college canteen manager and business planner.
</role>

<objective>
Design a practical 7-day operation plan for a college canteen using an initial budget of ₹10,000.
The plan must keep food affordable, tasty, hygienic, and profitable while handling uncertain student demand.
</objective>

<assumptions>
State all assumptions explicitly before the plan. At minimum, include:
- total number of students served per day
- average daily footfall pattern
- expected peak-hour demand
- any assumptions about ingredient sourcing, prep losses, and waste

Use realistic numbers for a college environment and do not assume a single-day spike that cannot be sustained for a week.
</assumptions>

<requirements>
Create a 7-day canteen plan that includes:
1. Menu: 6–8 popular food and drink items for college students
2. Pricing: affordable selling prices and estimated profit margin for each item
3. Quantities: number of portions to prepare per item per day
4. Budget: full ₹10,000 budget allocation and usage breakdown
5. Daily operations: daily cost, expected revenue, and expected profit for each day
6. Demand management: strategies for peak demand, sold-out items, low-demand items, and sudden demand changes
7. Waste control: methods to reduce spoilage and repurpose leftovers
8. Student satisfaction: quick service, variety, hygiene, and affordability

The plan must be financially sustainable over one week and should not spend the full budget on a single day.
</requirements>

<constraints>
- Initial spending must not exceed ₹10,000.
- Selling prices must be realistic for college students.
- Show calculations clearly for cost, pricing, margin, and daily totals.
- Keep the plan practical and operationally feasible.
- Do not invent unrealistic student volumes or unrealistic ingredient costs.
- If a value is uncertain, state the assumption explicitly and explain how it affects the plan.
</constraints>

<output_format>
Return the answer in Markdown with the following sections in this exact order:

1. Assumptions
2. Menu and Pricing Table
3. Daily Production Plan
4. 7-Day Budget and Revenue Summary
5. Demand Management Strategy
6. Waste Control Strategy
7. Student Satisfaction Strategy

Use a clean markdown table for menu, costs, and daily economics.
Include columns for: Item, Estimated Cost per Unit, Selling Price, Margin %, Daily Quantity, Daily Cost, Daily Revenue, Daily Profit.

For the 7-day summary, include:
- total spending
- total revenue
- total profit
- remaining budget
- waste estimate
- stock risk notes

Keep the response concise but detailed enough to be actionable.
</output_format>

<quality_bar>
Before finalizing, verify that:
- all calculations are internally consistent
- the total spend does not exceed ₹10,000
- daily quantities support realistic demand
- the menu includes a balanced mix of low-cost and high-margin items
- assumptions are stated clearly
- the plan prioritizes sustainability over short-term overbuying
</quality_bar>
```

## Final Assessment

This prompt is already usable and clearly aligned with the task. It would generate a good answer, but it could be significantly more consistent and robust with stricter formatting rules, explicit assumptions, and a clear schema. The most valuable improvement is converting the free-form requirements into a structured specification with explicit expected output sections and handling for edge conditions.
