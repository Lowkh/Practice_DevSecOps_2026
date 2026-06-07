# Written Practical Questions: DevSecOps and QA for Non-Technical Participants

## Purpose

This practical is a written exercise for non-technical participants. It is designed to help learners understand **SAST**, **DAST**, and **SCA** through short scenarios and written answers instead of live tools, coding, or technical setup.

The aim is to help participants:

- recognise what kind of finding is being described,
- connect the finding to a user workflow,
- decide whether the issue is theoretical, reachable, or user-impacting,
- explain why the issue matters to QA, product, and release teams,
- write a short evidence-based QA report.

---

## What participants need

Participants only need:

- this practical document,
- the participant worksheet,
- the bug report template,
- a pen or keyboard to record answers.

No installation is required. No coding is required. No command line is required.

---

## Simple definitions

### SAST

**Static Application Security Testing** checks code before the application runs.

### DAST

**Dynamic Application Security Testing** checks a running application from the outside.

### SCA

**Software Composition Analysis** checks third-party components and dependencies.

### Theoretical, reachable, user-impacting

- **Theoretical** — the pattern or condition exists, but it is not yet clear whether it can really be reached in practice.
- **Reachable** — the issue appears connected to a real feature, path, or workflow.
- **User-impacting** — the issue may already affect users, accounts, data, or transactions.

---

## Instructions for participants

Read each scenario carefully and answer the written questions in plain language. Participants should complete all three scenarios.

For each scenario, think about:

1. What was found?
2. Is the finding SAST, DAST, or SCA?
3. Which workflow, component, or dependency is affected?
4. Is the issue theoretical, reachable, or user-impacting?
5. What evidence supports the conclusion?
6. Should this affect release confidence? Why?

---

# Scenario 1

A prepared runtime test note says:

> “A test endpoint returned account information without the expected login check. The response was observed in a running test environment.”

### Extra context

The team is testing a deployed version of the application in a non-production environment. During testing, a response was observed that included account information even though the tester was not meant to have normal access to that data through the expected login flow.

The product owner first assumed this might only be a minor functional issue because the page did return a response. QA now needs to help clarify whether the issue is really about correctness, security exposure, or both.

### Points to think about

- The issue was seen in a running environment rather than in source code review.
- The main concern is not a broken screen; it is that information may have been exposed without the expected access check.
- Participants should think about which users or roles are supposed to see this information.
- Participants should also think about what evidence would make this finding credible to a release or product team.

## Questions

1. What was found?
2. Is this SAST, DAST, or SCA?
3. Which workflow is affected?
4. Who could be affected?
5. What evidence supports the conclusion?
6. Should this affect release confidence? Why?

---

# Scenario 2

A prepared dependency review note says:

> “Package lib-c version 4.0.0 is marked critical. A fixed version 4.0.3 exists. The service using it supports checkout.”

### Extra context

The application uses several third-party packages behind the scenes. A review of dependency information shows that one package used by the checkout service is marked as critical risk, and a newer fixed version is already available. No customer-visible failure has been reported yet.

Some team members assume this may be less important than a visible bug because customers have not complained. QA has been asked to help explain why dependency findings may still matter, especially when they affect a workflow connected to payments or transactions.

### Points to think about

- The issue is about a package and version, not a code snippet or a runtime screenshot.
- A fixed version already exists, which may affect urgency.
- The affected workflow is checkout, which is often business-critical.
- Participants should think about why software can inherit risk from components it depends on.

## Questions

1. What was found?
2. Is this SAST, DAST, or SCA?
3. Which workflow is affected?
4. Why does dependency risk matter here?
5. What evidence supports the conclusion?
6. Should this affect release confidence? Why?

---

# Scenario 3

A prepared code review note says:

> “User input from the search box is inserted directly into a database query string. The search feature appears to work in normal testing, but the pattern is unsafe.”

### Extra context

The team is reviewing a search feature before release. Functional testing shows that users can type a product name into the search bar and receive results normally. However, a security-related review note warns that the way the input is handled in code may be unsafe even though the visible feature appears to work as expected.

The release team is unsure whether this should be treated as a real defect because no obvious failure happened during ordinary testing. QA has been asked to help explain what the finding means, what workflow it affects, and whether it should influence release confidence.

### Points to think about

- The feature still works for normal users.
- The concern came from a code-related review, not from a runtime screenshot or a package list.
- The question is not only “Does the feature work?” but also “Is the way it handles user input safe?”
- Participants should think about whether a risky pattern can matter even before a confirmed exploit is shown.

## Questions

1. What was found?
2. Is this SAST, DAST, or SCA?
3. Which workflow is affected?
4. Is the issue theoretical, reachable, or user-impacting?
5. What evidence supports the conclusion?
6. Should this affect release confidence? Why?

---

# Final written task

Complete **all three** scenarios, then write a short comparative QA summary that covers all three findings.

Use the following headings:

- **Scenario 1 finding**
- **Scenario 2 finding**
- **Scenario 3 finding**
- **Which finding seems most urgent?**
- **Which finding has the clearest user or business impact?**
- **What evidence makes each finding credible?**
- **How should all three affect release confidence?**

---

# Reflection questions

1. Why is a feature not automatically safe just because it works?
2. Why is earlier discovery useful?
3. How can QA help without becoming a security specialist?
4. Which scenario felt easiest to understand, and what made it clearer than the others?
5. Which kind of evidence felt most convincing to you: code review notes, runtime observations, or dependency data?
