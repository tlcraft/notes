# Quality

Here are notes on building quality into software. From processes to bug ticket creation.

## Contents

- [Testing and Release Life Cycle](#testing-and-release-life-cycle)
- [Creating Bug Tickets](#creating-bug-tickets)
- [Boundary Value Analysis and Equivalence Partitioning](#boundary-value-analysis-and-equivalence-partitioning)
- [Baseline Bugs](#baseline-bugs)
- [Testing Pyramid](#testing-pyramid)
- [Project Management Triangle](#project-management-triangle)

## Testing and Release Life Cycle

To help ensure a high level of quality, testing needs to be done at all phases throughout development and the release process. Below is an overview of the areas where testing should occur. This is just one possible release process and can be adapted to unique situations. Different teams employ different strategies depending on their team makeup and structure. Building a suite of automated end-to-end tests will help reduce manual testing time as well.

- Important Points
    - Communication is key! Keeping teams in sync on our progress is important. Use team channels to communicate how things are going.
    - Regression testing in Dev and Test prior to UAT is very important! We can catch any bugs before UAT and it helps build trust with everyone around the organization. We want to deliver a high quality product!
    - Releasing working software is probably the most important thing that we do together. It involves everyone, from the initial developers implementing a solution, to QA completing regression testing, to stakeholders reviewing our features in UAT. We’re all working together on this!

- Dev Testing
    - The first round of testing is done by the original developer as they work on the feature
    - This should include writing automated unit tests within the code itself
    - The developer should also be running their code locally to test the workflows manually
    - Tests should include positive, negative, and boundary test cases (but is not limited to only these types)
    - Pull requests and code reviews will also help reduce issues
- Peer Review
    - Once a ticket is completed, or as subtasks are completed and are ready for review, another member of the develoment team should be testing the changes
    - This may sometimes include testing feature branches locally or in a specific environment
    - This also includes testing the final product in the development environment before other QAs
    - Consider multiple peer reviews. For instance, an internal one with the developers who worked on a larger feature together, and a following review with anyone interested from the larger team
- Demo
    - The original developer should now demo their work in the development environment to product owners 
    - This ensures we are delivering what is expected
    - This should be done with relevant product owners, business analysts and stake holders when possible
    - This would ideally be a relatively quick meeting to review the original ticket and demo the workflow
    - If there are issues or required updates the developer will make changes and repeat the above steps
    - Another demo will be needed once the changes are in place
    - Once accepted the developer can promote their code to the next stages of the release process
    - The developer, release team, and product owner should work to add (or update) test steps to a regression checklist as needed
- Dev Env Regression Testing
    - Before deploying to Test a release team can complete a thorough round of regression testing in the development environment
    - This should include a review of the latest features so a regression checklist can be updated
    - Any issues can be triaged and fixed depending on severity
- Test Env Regression Testing
    - Once the changes look good in the development environment we can release to Test
    - We will ask developers to confirm that their features are aviable in Test after the deploy
    - A full round of regression testing will be completed by the release team
    - If there are issues developers will be notified and changes will be made
- UAT
    - Once regression testing is completed we can alert the product owners that user acceptance testing can begin (or be scheduled)
    - If there are issues developers will be notified and changes will be made
    - The release team will run through regression testing again
    - UAT consists of:
        - Full review of the developed features and changes
        - General regression and edge case testing
        - Changing various values/settings and trying things multiple times in different ways
        - Final sign off for a production deployment comes from the release team and leadership
- Deploy to Production
    - Once UAT has completed and is signed off we can move forward to production
    - A smoke test will be performed by the release team to ensure the production deploy succeeded and to check a few features at a high-level (this process should not modify data in any way)
    - Communications can be sent out letting the team know we’ve completed the deployment to production

## Creating Bug Tickets

When creating a bug ticket be sure to give it a descriptive name and include the steps to reproduce the bug consistently. Add the expected and actual results. Considering adding details like the browser used, build versions and DevTools details (such as console log error messages and network logs). Capture screenshots and video when possible. Consider gathering logs from other systems, such as AWS CloudWatch when appropriate. If possible, link to related pull requests or work items.

## Boundary Value Analysis and Equivalence Partitioning

Boundary value analysis and equivalence partitioning are techniques for breaking down a large set of test cases into more manageable groups. When writing or performing tests we want a good range of test cases so that each edge case is reviewed. At a high level you can think of valid inputs, invalid inputs and mixtures of these to help test workflows. Valid and invalid inputs can also be known as positive and negative test cases.

- [Boundary Value Analysis and Equivalence Partitioning](https://www.guru99.com/equivalence-partitioning-boundary-value-analysis.html)
- [Positive Testing and Negative Testing with Examples](https://www.guru99.com/positive-and-negative-testing.html)

## Creating Test Cases

Along with concepts like boundary value analysis and equivalence partitioning consider other edge cases. For example, if you're working with a form consider resetting the form along with validation logic when canceling changes. If a form's validation is dependent on the state of the form, and it's reset to an earlier state, you'll need to ensure the validation is reset with the state change. Consider if nested objects and arrays need to be handled separately. In some cases these need special handling because of the nested data. Step back and consider the full scope of the system. Where else is something used or displayed? Do multiple views rely on similar data and need to be regression tested? Perhaps these views are driven by a user role and their permissions? Or does some data appear in a report?

## Baseline Bugs

It's good to remember to baseline bugs against a higher level environment (like Stage/Impl) to see if a bug is new or not. Just compare how a feature is working across two environments. One clean environment running the last production build and an updated environment with the latest code. It will help give context and the team can better assess the impact (is this entirely new from current development or existing).

## Testing Pyramid

We can use a variety of automated tests to build confidence that our software is working as expected. Unit tests are typically done by the software developers themselves. Larger integration tests are typically done by software developers in test. They also write end to end tests that use frameworks like Selenium to interact with web browsers and perform tasks. Some amount of manual testing is always important to ensure things look good. 

Unit tests are the cheapest (in terms of time) and fastest to run. As you go up the pyramid integration and end to end tests take more time to implement and maintain. They can take a long time to run. In some cases, you may want to create separate build processes for different areas of your system. These can send reports to the team for review with the test results.

- [The Testing Pyramid](https://automationpanda.com/2018/08/01/the-testing-pyramid/)

## Project Management Triangle

It's always important to keep the project management triangle in mind. Time, quality and scope are directly related to each other and we have to balance them as best we can. And when we can't we have to understand what we're sacrificing.

- [Project Management Triangle](https://en.wikipedia.org/wiki/Project_management_triangle)
