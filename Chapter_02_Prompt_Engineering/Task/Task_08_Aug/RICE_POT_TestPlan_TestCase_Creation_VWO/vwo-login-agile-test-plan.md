# VWO Login — Agile Test Plan

| Field | Value |
|---|---|
| **Project / Product Name** | VWO — Login Functionality |
| **Release / Sprint** | [Not Verifiable] |
| **Version** | [Not Verifiable] |
| **Prepared By** | [Not Verifiable] |
| **Date** | [Not Verifiable] |

> **Grounding note:** Only the login page controls listed in the task brief are treated as confirmed. All other behaviors, rules, limits, and project data are marked **[Dependency]**, **[Assumption]**, or **[Not Verifiable]**. No real credentials, tokens, or sensitive data are included.

---

## 1. Test Plan Overview

- **What is being tested:** The VWO login functionality at https://app.vwo.com/#/login — all visible login controls and sign-in methods: Email/Password, password visibility, Remember Me, Forgot Password, Sign In, Sign in with Google, Sign in using SSO, Sign in with Passkey, and the "New to Wingify — Start a free trial" link.
- **Why testing is required:** Login is the entry point to the application; a defect here blocks all users and is the primary target of credential attacks. It is a high-risk, high-impact control point.
- **Testing objective:** Validate the login experience end-to-end — functional, authentication, security, UI/usability, accessibility, compatibility, and regression — using risk-based, execution-oriented testing. Actual application behavior is the source of truth; anything unverifiable is explicitly marked, never assumed as fact.

---

## 2. Scope

### 2.1 In-Scope

| Feature / Functionality | Description | Priority |
|---|---|---|
| Email / Password login | Valid and invalid credential combinations, field validation, error handling | High |
| Password visibility | Toggle to reveal/hide password input **[Assumption — toggle presence to be verified]** | High |
| Remember Me | Session persistence behavior with and without the option selected | Medium |
| Forgot Password | Link navigation and reset flow behavior | High |
| Sign In | Form submission, loading states, error handling, post-login navigation | High |
| Google Login | Redirect flow, consent, success/failure handling | High |
| SSO Login | SSO redirect flow, success/failure handling **[Dependency — requires provisioned tenant]** | High |
| Passkey Login | Device-based authentication flow **[Dependency — requires passkey-configured device]** | High |
| Start a free trial link | Navigation to the sign-up/trial flow | Low |
| Privacy Policy / Terms link | Link presence, navigation, and behavior | Low |
| Security | Generic errors (no account enumeration), password masking, no credential exposure in DOM/URL/storage, repeated-attempt handling | High |
| Session | Session persistence on refresh, logout invalidation, idle timeout | Medium |
| UI / Usability | Layout, responsive behavior, keyboard navigation, Enter-to-submit, visual consistency | Medium |
| Accessibility | Keyboard-only operation, accessible names/labels (AX tree) | Medium |
| Compatibility | Chrome, Firefox, Edge, Safari; desktop/tablet/mobile viewports **[Assumption — browser matrix]** | High |
| Smoke / Sanity | Critical login flows prior to broader execution | High |
| Exploratory | Unscripted probing of login behaviors and edge cases, findings logged as defects | Medium |
| Regression | Critical login suite re-run after related changes | High |

### 2.2 Out of Scope

- In-application functionality after authentication (e.g., dashboard, settings, account admin)
- Load, performance, and stress testing; API-level testing
- Native mobile applications
- Non-English locale testing
- Admin-side configuration of SSO, 2FA, account policies, and identity providers
- Sign-up/trial form validation (only the login-page link navigation is in scope)
- Any authentication method not listed in the task brief

---

## 3. Test Approach / Strategy

Risk-based, execution-oriented manual testing with the live application as the primary source of truth; behaviors that cannot be verified are marked **[Dependency]** / **[Assumption]**.

| Area | Approach |
|---|---|
| Test levels | Component/system-level functional verification of the login page; smoke/sanity at the start of execution, regression at the end and after fixes |
| Manual vs Automation | Manual execution; automation **[Dependency]** — if automation is introduced, critical login flows (valid/invalid login, blank-field validation, Forgot Password navigation) are the first candidates |
| Functional | Verify every in-scope control and sign-in flow, positive and negative |
| Authentication | Email/password, Google, SSO, Passkey, MFA/OTP if applicable **[Assumption]**, account status handling (disabled/deleted **[Assumption]**) |
| Authorization / Access Control | Post-login access is out of scope; on the login page, verify unauthenticated users cannot bypass login to reach protected content |
| Security | Generic error consistency (no enumeration), password masking, no plaintext credentials in DOM/URL/storage, repeated-failure handling, no sensitive data in URLs |
| UI / Usability | Visual consistency, responsive layout, keyboard navigation, Enter submit |
| Accessibility | Keyboard-only operation, accessible names via the DevTools AX tree; full WCAG audit **[Dependency]** |
| Compatibility | Same flows across Chrome, Firefox, Edge, Safari and desktop/tablet/mobile viewports **[Assumption]** |
| Regression | Critical login suite re-run on each build/change; scope and frequency per Section 10 |
| Smoke / Sanity | Critical paths (valid login, invalid login, blank validation, Forgot Password, presence of all sign-in options) before deeper testing |
| Exploratory | Ad-hoc testing of edge cases (paste, autofill, tab behavior, multiple tabs); findings logged as defects with repro steps |
| Tools | Browser DevTools (Network, Application/Storage, AX tree) for verification; no external test tooling confirmed |

---

## 4. Test Environment

| Item | Details |
|---|---|
| Application URL | https://app.vwo.com/#/login (live application) |
| Test environment | Live production application **[Dependency — no separate QA/test environment confirmed]** |
| Browsers / devices | Chrome, Firefox, Edge, Safari (latest stable) **[Assumption]**; desktop (1920×1080, 1366×768), tablet (768×1024), mobile (375×667) **[Assumption]** |
| Test data | Placeholders only: valid test account (e.g., `qa.user@example.com` / `Placeholder@123`), unregistered email, invalid email formats, SSO/passkey/MFA-enabled accounts **[Dependency — provisioning required]** |
| Tools | Browser DevTools (Network, Application/Storage, Accessibility tree); defect tracking tool **[Not Verifiable]** |
| Automation / CI | **[Not Verifiable]** — no automation framework or CI tooling confirmed |

---

## 5. Entry & Exit Criteria

**Entry Criteria**
- VWO login page is accessible in the test environment
- Required test accounts (valid, invalid, disabled **[Assumption]**, MFA **[Assumption]**, SSO, passkey) are provisioned **[Dependency]**
- Test data and browser tooling available; environment stable

**Exit Criteria**
- All High-priority test cases executed; failures logged and triaged
- All critical/major defects fixed and verified (retest passed)
- No unresolved showstopper defects
- Test coverage summary completed and reviewed

---

## 6. Test Deliverables

| Deliverable | Status |
|---|---|
| Test Plan (this document) | Planned |
| Test Scenarios / Test Cases | To be created and executed |
| Automation scripts | **[Not Verifiable]** — no automation confirmed |
| Defect reports | Generated from execution (no fabricated data) |
| Test execution report | Produced at completion |
| Test summary | Produced at completion |

---

## 7. Roles & Responsibilities

| Role | Responsibility |
|---|---|
| QA Test Lead (author) | Test planning, strategy, execution oversight, defect triage facilitation, sign-off recommendation |
| QA Tester | Test case execution, defect logging, retesting, regression execution |
| Developer | Defect fixes and verification support |
| Product Owner / BA | Requirement clarification and priority decisions |
| Scrum Master | Coordination, removal of blockers |

**[Not Verifiable]** — named individuals and team assignments are not confirmed.

---

## 8. Risks & Dependencies

| Risk / Dependency | Impact | Mitigation |
|---|---|---|
| Live production app may change without notice | Test results may not reflect the latest build | Treat the live app as source of truth; capture actual behavior and message text at execution |
| No separate QA environment confirmed **[Dependency]** | Cannot isolate test data or destructive scenarios | Use placeholder/test accounts only; avoid destructive actions |
| SSO, Passkey, and MFA flows require enterprise provisioning **[Dependency]** | Cannot verify without a configured tenant/device | Verify on provisioned accounts; otherwise mark scenarios as Not Verifiable |
| Field limits, validation rules, lockout thresholds, and session timeouts not specified | Expected results cannot be predefined | Record actual values at execution and flag as Dependencies |
| Repeated failed logins may trigger rate limiting / lockout | Test accounts may be temporarily blocked | Space out attempts; use multiple test accounts |
| Bot detection / CAPTCHA may interrupt sessions | Automated steps fail | Handle manually; document observed behavior |
| No defect tracking or CI tooling confirmed **[Not Verifiable]** | Workflow overhead | Define minimal tracking (e.g., project issue board) at kickoff |

---

## 9. Defect Management

| Area | Approach |
|---|---|
| Defect logging | Log all defects with steps to reproduce, actual vs expected result, environment, severity, priority, and evidence |
| Severity / Priority | Standard 4-level scales; no project-specific SLA values invented |
| Triage | In sprint review/triage; decisions per sprint plan **[Not Verifiable]** |
| Retesting | After each fix, retest the original scenario; verify no adjacent breakage |
| Regression | Re-run critical login suite after each fix batch |
| Closure / Reopening | Close only after retest passes; reopen if a verified defect recurs |
| Blocking QA sign-off | Any showstopper, unresolved High-priority defect, or unverified critical login flow blocks sign-off |

---

## 10. Regression Strategy

| Area | Details |
|---|---|
| Regression scope | All in-scope login flows; critical focus on valid/invalid login, blank-field validation, Forgot Password navigation, presence and entry of all sign-in methods, Remember Me, and session behavior |
| Frequency | On each build/change affecting login or auth, and before release; smoke suite before every deeper cycle **[Dependency — build cadence not confirmed]** |
| Manual vs automated | Manual regression **[Assumption]**; automation to be evaluated **[Dependency]** |
| Critical login functionality included | Yes — valid login, invalid credentials, blank mandatory fields, Forgot Password, Google/SSO/Passkey entry points, Remember Me persistence, logout invalidation |

---

## 11. Test Summary

Metrics to be captured at completion (not populated — no fabricated results):

| Metric | Value |
|---|---|
| Total test cases | |
| Executed | |
| Passed | |
| Failed | |
| Blocked | |
| Defects found | |
| Defects fixed | |
| Defects deferred | |
| Overall QA status | |

---

## 12. Requirements Traceability

Traceability will follow: **Requirement → Test Scenario → Test Case → Defect**.

Complete RTM cannot be established: formal requirements and sprint documentation are **[Not Verifiable]**. Requirement identifiers will be mapped to test scenarios/cases during execution once the requirements baseline is confirmed.

---

## 13. Sign-off

| Role | Status | Date | Notes |
|---|---|---|---|
| QA Test Lead | | | |
| Developer | | | |
| Product Owner / BA | | | |

No names or approval statuses are fabricated; sign-off authority is **[Not Verifiable]**.
