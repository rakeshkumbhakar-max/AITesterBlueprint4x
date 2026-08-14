## RICE POT Prompt– VWO Login Test Plan & Test Case Creation

R → ROLE : You are a Senior QA Test Lead with 15+ years of experience in Web Application Testing, Functional Testing, Negative Testing, UI Testing, Authentication, Security, Regression Testing, and Agile/Scrum. Create an industry-level Test Plan and comprehensive Test Cases for the VWO Login page.
I → INSTRUCTIONS

• Analyze the VWO Login page: https://app.vwo.com/#/login
• Identify all visible controls and applicable login functionality.
• Cover positive, negative, boundary, validation, UI, authentication, security, session, usability, accessibility, and regression scenarios.
• Cover:
  - Email
  - Password
  - Password visibility
  - Forgot Password
  - Remember Me
  - Sign In
  - Sign in with Google
  - Sign in using SSO
  - Sign in with Passkey
• [Mandatory] Verify mandatory fields, invalid inputs, valid/invalid credentials, error handling, navigation, and access control.
• [Don't] Do not invent validation messages, business rules, field limits, or application behavior.
• [Critical] If functionality cannot be verified, clearly mark it as an assumption or dependency.
• Avoid duplicate or redundant test cases.
• Each test case must be independent, executable, and have a clear expected result.
• Use realistic test data and placeholders for credentials.
• [Don't] Do not expose passwords, tokens, or other sensitive information.

C → CONTEXT

You are creating an industry-level Test Plan and Test Cases for the VWO Login page at https://app.vwo.com/#/login. The VWO Login page is an authentication interface that provides users with multiple methods to access the VWO application. The objective is to validate the complete login experience from a functional, security, and user perspective. The provided screenshot should be used as a reference for the Login page UI and available controls, while the actual application behavior should be treated as the primary source of truth.
E → EXAMPLE
•	Test Case Format

TID	Category	Description	Pre-conditions	Steps	Expected	Priority
VWO-TC-001	Functional	Verify login with valid credentials	Valid account exists	1. Open the login page.2. Enter valid email and password.3. Click Sign In.	User is successfully authenticated and redirected to the appropriate page.	High
VWO-TC-002	Validation	Verify login with blank Email	Login page is displayed	1. Leave Email blank.2. Enter a valid password.3. Click Sign In.	Appropriate validation is displayed and login is not successful.	High

Use this exact format for all test cases.

P → PARAMETERS

•	Generate:

- 1 Test Plan
- Comprehensive Test Scenarios
- Detailed Test Cases
- Test Coverage Summary

•	Test cases must cover:

- Positive Testing
- Negative Testing
- Boundary & Validation Testing
- Functional Testing
- UI Testing
- Authentication Testing
- Authorization/Security Testing
- Session Testing
- Forgot Password
- Remember Me
- Google Login
- SSO Login
- Passkey Login
- Cross-Browser Testing
- Accessibility/Usability
- Regression Testing

•	Prioritize each test case as:

- High
- Medium
- Low

Target approximately 30–50 meaningful test cases. Prioritize coverage and quality over quantity.

O → OUTPUT

•	Generate the output in the following order:

1. TEST PLAN

Include only:

- Objective
- Scope
- In-Scope
- Out-of-Scope
- Test Strategy
- Test Types
- Test Environment
- Test Data
- Entry Criteria
- Exit Criteria
- Risks & Mitigation
- Assumptions/Dependencies

2. TEST SCENARIOS

•	Provide a concise table:

| SID | Category | Test Scenario | Priority |

3. TEST CASES

•	Use exactly this format:

| TID | Category | Description | Pre-conditions | Steps | Expected | Priority |

•	Do not add or remove columns.

•	Steps must be numbered within the table cell.

4. TEST COVERAGE SUMMARY

•	Summarize coverage for:

- Functional
- Positive
- Negative
- Validation
- Authentication
- Security
- Session
- UI/Usability
- Accessibility
- Compatibility
- Regression

T → TONE

Technical, concise, precise, professional, and industry-level QA/Test Lead standard.

Do not provide chain-of-thought or internal reasoning.

Do not provide unnecessary explanations.

Generate only the requested Test Plan, Test Scenarios, Test Cases, and Test Coverage Summary.
