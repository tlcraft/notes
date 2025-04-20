# Quality

Here are notes on building quality into software. From processes to bug ticket creation.

Contents

- [Testing and Release Life Cycle](#testing-and-release-life-cycle)
- [Creating Bug Tickets](#creating-bug-tickets)

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
