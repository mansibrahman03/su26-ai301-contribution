# Contribution #1: MFlowCode

**Contribution Number:** 1 
**Student:** Mansib Rahman  
**Issue:** https://github.com/MFlowCode/MFC/issues/1508 
**Status:** Complete

---

## Why I Chose This Issue

I chose this issue because it matches my technical skills. I am proficient in Python, have experience building projects with jupyter notebooks, and am comfortable using Shell. The issue description is clear to me and I know exactly what bugs I need to fix. I liked the step by step description of the problems, provided by the owner of the codebase. These are problems that seem familiar to me as I have solved similar problems while working on personal projects.

---

## Understanding the Issue

### Problem Description

The repetition of the verbose idiom "self.get("name", "F") == "T"" in case_validator.py made the code hard to read and more prone to error. 

### Expected Behavior

I expect the computer to know what to do when it is given a function like flag() and output the correct result.

### Current Behavior

The terminal blanks and doesn't output anything when the flag() method.

### Affected Components

I will need to edit case_validator.py and ast_analyzer.py. Specifically, I will need to implemented a helper method called flag() in case_validator.py and edit the _build_local_param_map() method in ast_analyzer.py.

---

## Reproduction Process

### Environment Setup

I did not face any problems during the environment setup process.

### Steps to Reproduce

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

There is an unnecessary repetition of the idiom "self.get(x,F)==T" in case_validator. To fix this, I must implement a flag() method. This method must also be recognized in other files. Specifically, I must edit the _build_local_param_map method in ast_analyzer to recognize flag().

### Proposed Solution

I will add a flag() method in toolchain/mfc/case_validator.py that functions to replace the verbose idiom "self.get(x,F)==T" repeated in 134 places across the file. Additionally, I will update ast_analyzer.py to recognize calls made to flag().

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** At the moment, case_validator.py reads boolean case flags with the verbose form self.get("name", "F") == "T" in 134 places. To clean this code up I want to implement a map function. However, I am prevented from doing so at the moment because of the hard coding in ast_analyzer.py in the _build_local_param_map() method in line 232: call.func.attr == "get". Thus, when the analyzer sees the word "flag", it doesn't recognize it and blanks out.

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. My solution is to first make sure the analyzer recognizes flag() by adding a conditional statement in _build_local_param_map() in ast_analyzer.py.
2. Next I will implement a flag() method in case_validator.py that maps the verbose form to a simple boolean value.
3. Finally, I will write tests to ensure flag() functions as expected and is recognized in ast_analyzer.

**Implement:** https://github.com/MFlowCode/MFC/compare/master...mansibrahman03:MFlowCode:main

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** I will verify my approach works by calling flag() instead of get() in line 1487 of case_validator.py. If the analyzer correctly returns a value instead of blank, it successfully recognized the flag() function. I will also test the flag() method itself to ensure it correctly returns true or false.

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
