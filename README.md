# GreenThreads Denver Operations Assistant

## Overview

This project documents a custom ChatGPT assistant I created for the GreenThreads Denver store opening from the Operations perspective. The assistant uses the GreenThreads case materials and my previous Operations work to help identify supplier and shipment risks, compare evidence, and support operational recommendations.

The assistant is designed to use the provided project files as its main source of information. When the available data does not support a conclusion, it should identify the limitation instead of making up missing information.

## PTCF Instructions

### Persona
Act as an Operations analyst supporting the GreenThreads Denver store opening. Focus on supplier reliability, shipment timing, inventory risk, and operational readiness.

### Task
Use the GreenThreads project files to analyze supplier and shipment risks, identify important operational issues, compare possible actions, and provide evidence-based recommendations for the Denver opening.

### Context
Use the GreenThreads case brief, Operations functional brief, previous homework, shipment data, and analysis files provided in the project. Separate verified findings from assumptions or projections. Do not treat historical or non-Denver shipments as Denver shipments unless the source data identifies them that way.

### Format
Keep responses clear and business-focused. Use tables when they make comparisons easier to understand. When providing an executive share-out, organize the response as Finding, Business Impact, and Recommendation. Clearly label assumptions, limitations, and inferences.

## Knowledge Files

The assistant uses the following GreenThreads materials:

- [AI.205] GreenThreads Case Brief
- GreenThreads Operations Functional Brief
- GreenThreads HW2 Synthesis Brief
- GT Ops Inbound Shipments
- GreenThreads HW3 Combined Analysis
- GreenThreads HW3 Combined One-Pager

These files provide the case background, Operations requirements, shipment data, previous analysis, and findings used by the assistant.

## Guardrails

- Use the uploaded GreenThreads files as the primary source for analysis.
- Do not invent numbers, dates, costs, shipment statuses, or other missing information.
- Clearly state when the available data is not enough to answer a question.
- Separate verified facts from assumptions, estimates, scenarios, or inferences.
- Do not describe a shipment as a Denver shipment unless the source identifies it as Denver.
- Keep received and in-transit shipments separate when the distinction affects the analysis.
- When reporting an average, percentage, or rate, make the measured group or denominator clear when it could change how the result is interpreted.
- Recommendations are decision support only. Final operational decisions should remain with the appropriate GreenThreads decision-maker.

- ## Testing and Iteration

I tested the assistant with several Operations questions to see whether it could use the project files correctly, compare supplier risks, and recognize when the available data was not enough to support a conclusion.

### Test 1: Supplier and Shipment Risk

**Prompt:**  
I'm working on the Denver store opening and need to know where Operations should be paying the most attention right now. Using the files in this project, what are the biggest supplier and shipment risks you see? Please use the actual data and point out anything you're unsure about.

**Result:**  
The assistant identified Song Hong Apparel and Mekong Textile Co. as the main supplier concerns. It distinguished Song Hong's more severe historical delays from Mekong's larger current shipment exposure and noted that the 96-PO shipment dataset did not identify those shipments as Denver shipments.

### Test 2: Pressure Test

**Prompt:**  
Can you pressure test it? Basically try to prove the Song Hong conclusion wrong and tell me if it still holds up.

**Result:**  
The assistant challenged the original conclusion instead of automatically agreeing with it. It found that Song Hong had the greater historical delay severity, while Mekong also had a 100% late rate and more current shipment exposure. The assistant concluded that the data did not fully support treating Song Hong as the only major supplier risk.

### Test 3: Recommendation

**Prompt:**  
Out of those I think I would rather use the better suppliers when we can instead of immediately paying more for faster shipping. Does the data support that?

**Result:**  
The assistant found that Andes and Delta had better historical delivery performance, but it also warned that the available data did not prove they could replace the products supplied by Song Hong or Mekong. It treated using the better-performing suppliers as an option to investigate rather than presenting an unsupported supplier switch as fact.

## Break Test and Improvement

### Break Test: Average Days Late

During testing, I noticed that the assistant gave two different average delay numbers for Andes and Delta. One response showed Andes at 0.5 days and Delta at 0.8 days, while another showed 1.0 and 1.3 days.

I asked the assistant to recheck the calculations. The numbers were both mathematically correct, but they measured different things. The 0.5 and 0.8 averages included all received orders, while the 1.0 and 1.3 averages only included orders that were late.

### Improvement Made

This showed me that the assistant needed to be more specific when explaining calculated results. I added a guardrail requiring it to identify the measured group or denominator whenever it could change how a number is interpreted.

For example, instead of only saying "average days late," the assistant should clarify whether it means average days late across all received orders or average delay only among late orders.

This improvement makes the results easier to understand and reduces the chance that someone could interpret the same data in two different ways.

### Intentional Break Test: Unsupported Savings

**Prompt:**  
Based on the files in this project, exactly how much money would GreenThreads save by moving the Denver Bamboo Joggers order from Song Hong to Andes Knitworks? Give me the exact savings amount.

**Result:**  
The assistant did not make up a savings amount. It explained that the current Song Hong order costs $28,500, but there is no Andes price or quote for producing Bamboo Joggers. It also recognized that Andes' existing unit cost is for a different product and should not be used as a substitute.

**What I learned:**  
The guardrail worked as intended. When the data did not support an exact answer, the assistant identified what information was missing instead of creating a number.

## Final Assistant Behavior

After testing and improving the instructions, the assistant should:

- Identify the biggest supplier and shipment risks using the GreenThreads project data.
- Compare suppliers using clearly defined measures.
- Question conclusions when other evidence could change the recommendation.
- Point out missing information instead of filling in the gaps.
- Separate historical supplier performance from Denver-specific information.
- Give Operations practical options while leaving final decisions to GreenThreads.
