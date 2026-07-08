# Contribution [#1]: [Issue Title]

**Contribution Number:** 1 
**Student:** Mansib Rahman  
**Issue:** https://github.com/tinaudio/synth-setter/issues/51 
**Status:** [Phase I] [Complete]

---

## Why I Chose This Issue

[1-2 paragraphs explaining why this issue interests you, how it matches your skills/learning goals, what you hope to learn]

I chose this issue because it matches my technical skills. I am proficient in Python, have experience building projects with jupyter notebooks, and am comfortable using Shell. The issue description is clear to me and I know exactly what bugs I need to fix. I liked the step by step description of the problems, provided by the owner of the codebase. These are problems that seem familiar to me as I have solved similar problems while working on personal projects.

---

## Understanding the Issue

### Problem Description

[In your own words, what's broken or missing?]

### Expected Behavior

[What should happen?]

### Current Behavior

[What actually happens?]

### Affected Components

[Which parts of the codebase are involved?]

---

## Reproduction Process

### Environment Setup

I did not face any problems during the environment setup process.

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]
1. Open the file case_validator.py using the file path toolchain/mfc/case_validator.py
2. Go to line 1487 in the check_chemistry() method
3. Replace the value assigned to the chemistry variable with self.flag("chemistry")
4. Reproduce the issue on your terminal by running the following: python3 toolchain/mfc/gen_case_constraints_docs.py | grep "ANALYZER"

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** The terminal blanks and doesn't output anything when the flag() method is called. I expect the computer to know what to do when it is given a function like flag() and output the correct result.

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

1. At the moment, case_validator.py reads boolean case flags with the verbose form self.get("name", "F") == "T" in 134 places. To clean this code up I want to implement a map function. However, I am prevented from doing so at the moment because of the hard coding in ast_analyzer.py in the _build_local_param_map() method in line 232: call.func.attr == "get". Thus, when the analyzer sees the word "flag", it doesn't recognize it and blanks out.

2. My solution is to first make sure the analyzer recognizes flag() by adding a conditional statement in _build_local_param_map() in ast_analyzer.py. I will then implement a flag() method in case_validator.py that maps the verbose form to a simple boolean value.

3. Files I will touch include:
   - case_validator.py
   - ast_analyzer.py
     
4. I will verify my approach works by calling flag() instead of get() in line 1487 of case_validator.py. If the analyzer correctly returns a value instead of blank, it successfully recognized the flag() function. I will also test the flag() method itself to ensure it correctly returns true or false.

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
