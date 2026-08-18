# VWO Login — Agile Test Plan

| Field | Value |
|---|---|
| **Project / Product Name** | VWO — Login Functionality |
| **Release / Sprint** | N/A — Standalone QA Test Exercise |
| **Version** | 1.0 |
| **Prepared By** | Rakesh Kumbhakar |
| **Date** | 14-Aug-2026 |

> **Documentation Note:** This Test Plan defines the QA approach for the VWO Login functionality within the stated scope. Application behavior, validation rules, and environment-specific details will be verified during test execution against the applicable application and requirements.

---

## 1. Test Plan Overview

- **What is being tested:** The VWO login functionality at https://app.vwo.com/#/login — all visible login controls and sign-in methods: Email/Password, password visibility, Remember Me, Forgot Password, Sign In, Sign in with Google, Sign in using SSO, Sign in with Passkey, and the "New to Wingify — Start a free trial" link.
- **Why testing is required:** Login is the entry point to the application; a defect here blocks all users and is the primary target of credential attacks. It is a high-risk, high-impact control point.
- **Testing Objective:** Validate the VWO Login experience through functional, positive, negative, validation, authentication, security, session, UI/usability, accessibility, compatibility, and regression testing using a risk-based testing approach.
- **Testing Approach:** Verify the defined login functionality against the approved scope and actual application behavior. Application-specific requirements, validation rules, error messages, and security controls will be validated during test execution rather than assumed.

---

## 2. Scope

### 2.1 In-Scope

| Feature / Functionality | Description | Priority |
|---|---|---|
| Email / Password login | Valid and invalid credential combinations, field validation, error handling | High |
| Password visibility | Toggle to reveal/hide password input | High |
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

Risk-based, execution-oriented testing will be used to validate the login functionality within the approved scope. Actual application behavior and approved requirements will be used as the basis for expected results.

| Area | Approach |
|---|---|
| Test levels | Component/system-level functional verification of the login page; smoke/sanity at the start of execution, regression at the end and after fixes |
| Manual vs Automation | Manual execution; automation **[Dependency]** — if automation is introduced, critical login flows (valid/invalid login, blank-field validation, Forgot Password navigation) are the first candidates |
| Functional | Verify every in-scope control and sign-in flow, positive and negative |
| Authentication | Email/password, Google, SSO, and Passkey authentication within the approved scope |
| Authorization / Access Control | Post-login access is out of scope; on the login page, verify unauthenticated users cannot bypass login to reach protected content |
| Security | Generic error consistency (no enumeration), password masking, no plaintext credentials in DOM/URL/storage, repeated-failure handling, no sensitive data in URLs |
| UI / Usability | Visual consistency, responsive layout, keyboard navigation, Enter submit |
| Accessibility | Keyboard-only operation, focus behavior, accessible names/labels, and applicable accessibility checks |
| Compatibility | Same flows across Chrome, Firefox, Edge, Safari |
| Regression | Critical login suite re-run on each build/change; scope and frequency per Section 10 |
| Smoke / Sanity | Critical paths (valid login, invalid login, blank validation, Forgot Password, presence of all sign-in options) before deeper testing |
| Exploratory | Ad-hoc testing of edge cases (paste, autofill, tab behavior, multiple tabs); findings logged as defects with repro steps |
| Tools | Browser DevTools for Network, Application/Storage, and accessibility verification; applicable test and defect management tools |

---

## 4. Test Environment

| Item | Details |
|---|---|
| Application URL | https://app.vwo.com/#/login  |
| Test Environment | Web application accessed through the provided VWO Login URL |
| Browsers / Devices | Chrome, Firefox, Edge, Safari; desktop |
| Test Data | Dedicated test accounts and representative positive/negative test data. Credentials will be stored securely and will not be committed to the repository. SSO and Passkey scenarios require appropriately configured test accounts/devices. |
| Tools | Browser DevTools (Network, Application/Storage, Accessibility tree); applicable test and defect management tools |
| Automation / CI | Not included in the current test cycle |

---

## 5. Entry & Exit Criteria

**Entry Criteria**
- VWO login page is accessible in the test environment
- Required test accounts for valid/invalid login, Google, SSO, and Passkey scenarios are available as applicable
- Required test data is available
- Required browsers and test devices/viewport configurations are available
- Test environment is accessible and reasonably stable

**Exit Criteria**
- All High-priority test cases executed; failures logged and triaged
- Critical defects are resolved and verified, or formally accepted as release risks
- No unresolved showstopper defects
- Test coverage summary completed and reviewed
- Blocked test scenarios and outstanding dependencies are documented and communicated

---

## 6. Test Deliverables

| Deliverable | Status |
|---|---|
| Test Plan | Ready for Review |
| Test Scenarios / Test Cases | To be created and executed |
| Automation Scripts | Not included in the current test cycle |
| Defect Reports | Created for defects identified during test execution |
| Test Execution Report | Prepared after test execution |
| Test Summary Report | Prepared after completion of testing |

---

## 7. Roles & Responsibilities

| Role | Responsibility |
|---|---|
| QA Test Lead (author) | Test planning, strategy, execution oversight, defect triage facilitation, sign-off recommendation |
| QA Tester | Test case execution, defect logging, retesting, regression execution |
| Developer | Defect fixes and verification support |
| Product Owner / BA | Requirement clarification and priority decisions |
| Scrum Master | Coordination, removal of blockers |


---

## 8. Risks & Dependencies

| Risk / Dependency | Impact | Mitigation |
|---|---|---|
| Application changes during testing | Test results may become outdated or impacted by changes | Confirm the application version/build where applicable and re-execute impacted scenarios after changes |
| Test environment availability | Testing may be blocked or test data may not be isolated | Use the designated test environment and dedicated test accounts where available |
| SSO and Passkey configuration | SSO or Passkey scenarios may be blocked without required account/device configuration | Execute these scenarios using appropriately configured test accounts and supported devices |
| Field limits, validation rules, lockout thresholds, and session timeouts not specified | Expected results cannot be predefined | Record actual values at execution and flag as Dependencies |
| Repeated failed logins may trigger rate limiting / lockout | Test accounts may be temporarily blocked | Space out attempts; use multiple test accounts |
| Bot detection / CAPTCHA may interrupt sessions | Automated steps fail | Handle manually; document observed behavior |


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
| Frequency | Execute regression after changes affecting login or authentication functionality and before release |
| Execution Approach | Regression may be executed manually or through approved automation; critical scenarios should be prioritized for automation where automation is available |
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

### 12. Requirements Traceability

Requirements will be traced through the following relationship:

**Requirement → Test Scenario → Test Case → Defect**

| **Traceability Item** | **Approach** |
|---|---|
| Requirement Source | Approved product requirements, user stories, acceptance criteria, and applicable specifications |
| Requirement Identification | Use approved requirement or user-story IDs where available |
| Test Scenario Mapping | Map each applicable requirement to one or more test scenarios |
| Test Case Mapping | Map test scenarios to executable test cases |
| Defect Mapping | Link defects to the affected test case and requirement where applicable |
| Coverage Review | Review requirement coverage before test completion and release sign-off |

---

## 13. Sign-off

| Role | Status | Date | Notes |
|---|---|---|---|
| QA Test Lead | | | |
| Developer | | | |
| Product Owner / BA | | | |

No names or approval statuses are fabricated; sign-off authority is **[Not Verifiable]**.
