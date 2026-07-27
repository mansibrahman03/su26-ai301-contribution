# Contribution #2: Great Expectations

**Contribution Number:** 2

**Student:** Mansib Rahman

**Issue:** https://github.com/fivetran/great_expectations/issues/11963  

**Status:** Phase II Complete

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

1. From the root of the directory, go to tests/integration/data_sources_and_expectations/expectations/test_expect_column_values_to_be_of_type.py 
2. Add a print statement that prints the test result from test_success_for_type__int()
3. Run the following command in your terminal: pytest tests/integration/data_sources_and_expectations/expectations/test_expect_column_values_to_be_of_type.py \ -k "test_success_for_type__INTEGER" -s
4. Observe the output

### Reproduction Evidence

- **Commit showing reproduction:** https://github.com/mansibrahman03/great_expectations/tree/fix-issue-11963
- **Screenshots/logs:**
  Reproduction code:
  <img width="1292" height="310" alt="image" src="https://github.com/user-attachments/assets/a197e2ef-00e8-4ef6-8e7f-e6d7e3a42d04" />
  Result 1:
  <img width="894" height="1144" alt="image" src="https://github.com/user-attachments/assets/67cf5d04-40e4-4104-a79b-5d58eb86b46a" />
  Result 2:
  <img width="862" height="830" alt="image" src="https://github.com/user-attachments/assets/3df2ee84-1adf-4e73-b135-5775c331d19f" />


- **My findings:** The ExpectColumnValuesToBeOfType performs schema-level validation on one pandas dataset and row-level validation on another.

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

- [ ] test_expectation_is_registered_and_constructible: the new expectation loads and can be created without errors
- [ ] test_validate_pandas_success: when a column's type matches what we asked for, it passes and reports the type it saw
- [ ] test_validate_pandas_failure_returns_schema_level_result: when the type doesn't match, it fails but still just reports the type it saw without row-level details
- [ ] test_validate_pandas_object_column_is_schema_level: a pandas text/mixed object column is checked by its overall type, not row by row
- [ ] test_prescriptive_renderer_template: the human-readable message reads like "column type must be X"

### Integration Tests

- [ ] Integration scenario 1: Gives just the column's type on pandas, SQL databases, and Spark
- [ ] Integration scenario 2: A pandas object column is judged by its declared type only, with no row-level details

### Manual Testing

<img width="2166" height="194" alt="image" src="https://github.com/user-attachments/assets/3e0e55b9-b225-49fc-b84b-d1e2a6cce247" />


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
