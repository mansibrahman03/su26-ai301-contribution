# Contribution [#2]: [Great Expectations]

**Contribution Number:** [2]  
**Student:** [Mansib Rahman]  
**Issue:** [https://github.com/fivetran/great_expectations/issues/11963]  
**Status:** [Phase I]

---

## Why I Chose This Issue

First, the problem is clear. The issue explains exactly whats missing and why it is needed. Importantly, this is primarily a python-based project, the language I am most proficient in. Furthermore, the issue aligns with the skills I have developed from past projects. It also involves libraries and concepts I am familiar with.

---

## Understanding the Issue

### Problem Description

Right now, the ExpectColumnValuesToBeOfType expectation two different kinds of checks depending on the backend. On Pandas, it goes through every value for every column and validates its type. On SQLAlchemy and Spark it only checks every column's declared type. Thus, one class is checking for completely different metrics depending on the backend.

### Expected Behavior

I expect for there to be 2 separate expectations: one that checks the declared type of the entire column and another that checks every row.

### Current Behavior

At the moment, the same expectation is responsible for either schema-level type validation or row-level type validation, depending on the backend. 

### Affected Components

This problem affects the type comparison logic used by Pandas, SQLAlchemy, and Spark. This can result in inconsistent behavior across data sources.

---

## Reproduction Process

### Environment Setup

I experienced errors while setting up the necessary dependencies for the codebase. I used AI assistance to fix these issues.

### Steps to Reproduce

1. Run the existing ExpectColumnValuesToBeOfType expectation on a SQL, Spark, or Pandas dataset
2. Compare the behavior across the different backends
3. Observe that the expectation performs schema-level validation on some backends and row-level validation on others

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:**
  <img width="1928" height="390" alt="image" src="https://github.com/user-attachments/assets/b9915049-42c7-4b95-92dd-4fb3493e9d8c" />
  <img width="2316" height="1104" alt="image" src="https://github.com/user-attachments/assets/d1ca131f-82eb-4e50-8a2f-c265b84a9cd0" />

- **My findings:** I observed that the expectation performs schema-level validation on some backends and row-level validation on others, resulting in inconsistent behavior across backends.

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

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
