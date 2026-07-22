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

1. Run the existing ExpectColumnValuesToBeOfType expectation on Pandas, SQL, and Spark datasets
2. Compare the behavior across the different backends
3. Observe that the expectation performs schema-level validation on some backends and row-level validation on others

### Reproduction Evidence

- **Commit showing reproduction:** https://github.com/mansibrahman03/great_expectations/tree/fix-issue-11963
- **Screenshots/logs:**
  These are the existing implementations
  <img width="1872" height="1568" alt="image" src="https://github.com/user-attachments/assets/817e2242-9b4d-41d5-9778-097938e5fe22" />
  <img width="1928" height="390" alt="image" src="https://github.com/user-attachments/assets/b9915049-42c7-4b95-92dd-4fb3493e9d8c" />
  <img width="1940" height="974" alt="image" src="https://github.com/user-attachments/assets/18333b07-0472-4441-b684-f430944f829e" />

- **My findings:** The same expectation performs schema-level validation on some backends and row-level validation on others, resulting in inconsistent behavior across backends.

---

## Solution Approach

### Analysis

The issue is caused by the way the ExpectColumnValuesToBeOfType expectation is implemented. At the moment, it can make either schema-level or row-level type checks depending on the backend.

### Proposed Solution

Create a separate ExpectColumnTypeToBe expectation that only performs schema-level validation. The existing ExpectColumnValuesToBeOfType expectation will only perform row-level validation.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** The current implementation of the ExpectColumnValuesToBeOfType expectation causes inconsistent behavior across different backends.

**Match:** I can reuse the existing type comparison logic for ExpectColumnValuesToBeOfType and follow the structure of existing expectation classes in implementing ExpectColumnTypeToBe.

**Plan:**
1. Create a new ExpectColumnTypeToBe expectation class
2. Review and use the existing type comparison logic
3. Add and update unit and integration tests
4. Verify existing expectations work correctly

**Implement:** https://github.com/mansibrahman03/great_expectations/tree/fix-issue-11963

**Review:** 
- Ensure the implementation follows the project's coding style and contribution guidelines
- Ensure implementation passes test requirements

**Evaluate:** 
- Run the relevant unit and integration tests to confirm that the new expectation and existing expectations behave correctly.
- Ensure existing functionality is not broken.

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
