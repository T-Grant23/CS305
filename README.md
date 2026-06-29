# CS305
Briefly summarize your client, Artemis Financial, and its software requirements. Who was the client? What issue did the company want you to address?
Artemis Financial is a financial consulting company that builds individualized financial plans (savings, retirement, investment, insurance) for its customers. Because they handle sensitive financial and personal data, they asked me to perform a vulnerability assessment on their Java-based REST API application to identify security weaknesses in the code and its dependencies.
-
What did you do well when you found your client’s software security vulnerabilities? Why is it important to code securely? What value does software security add to a company’s overall well-being?
I was thorough in tracing each manual review finding back to a specific class and line of reasoning (non-private fields in Customer.java and myDateTime.java, missing input bounds checks, unclosed DB connections, SQL injection risk in DocData.java), rather than just listing generic issues. Secure code matters because a single overlooked flaw, like an unvalidated input or an exposed variable, can expose customer financial data, damage trust, and create legal/regulatory liability. Strong security is a direct contributor to a company's reputation, customer retention, and bottom line.
-
Which part of the vulnerability assessment was challenging or helpful to you?
The dependency-check (static testing) step was the most helpful because it surfaced vulnerabilities I wouldn't have caught manually. Outdated libraries like spring-core, tomcat-embed-core, and snakeyaml carried dozens of CVEs each.
-
How did you increase layers of security? In the future, what would you use to assess vulnerabilities and decide which mitigation techniques to use?
I approached it in layers: manual code review for logic/design flaws (encapsulation, input validation, resource handling) plus automated dependency scanning for known, published vulnerabilities in third-party libraries. That combination catches both custom-code mistakes and inherited risk. Going forward, I'd keep using OWASP Dependency-Check alongside other static analysis tools.
-
How did you make certain the code and software application were functional and secure? After refactoring the code, how did you check to see whether you introduced new vulnerabilities?
After making the recommended changes (encapsulating fields, adding bounds/input checks, closing DB connections, removing duplicate code), I'd re-run the existing test suite to confirm functionality wasn't broken, then re-run the dependency-check scan to confirm CVE counts dropped and no new ones were introduced by version upgrades.
-
What resources, tools, or coding practices did you use that might be helpful in future assignments or tasks?
OWASP Dependency-Check for SCA scanning, secure coding practices like proper encapsulation, parameterized queries (to prevent SQL injection), input validation/bounds checking, and resource cleanup (closing connections/streams). The vulnerability assessment process-flow diagram itself is a reusable mental model for structuring future assessments.
-
Employers sometimes ask for examples of work that you have successfully completed to show your skills, knowledge, and experience. What might you show future employers from this assignment?
I would show them the completed vulnerability assessment report itself because it demonstrates the ability to read unfamiliar code, identify concrete security flaws with specific justification, interpret an automated vulnerability report, and translate findings into a prioritized, actionable mitigation plan.
