# Quality

Here are notes on building quality into software. From processes to bug ticket creation.

## Software Development Life Cycle

To help ensure a high level of quality, testing needs to be done at all phases throughout development and the release process. Below is an overview of the areas where testing should occur. This is just one possible release process and can be adapted to unique situations. Different teams employ different strategies depending on their team makeup and structure.

- Dev Testing
    - The first set of testing is with the original feature developer as they work on a ticket
    - This should include writing automated unit tests within the code itself
    - The developer should also be running their code locally to test the workflows manually
    - Tests should include positive, negative, and boundary test cases (but is not limited to only these types)
    - Pull requests and code reviews will also help reduce issues
- Peer Review
    - Once a ticket is completed, or as subtasks are completed and are ready for review, another member of the develoment team should be testing the changes
    - This may sometimes include testing feature branches locally or in a specific environment
    - This also includes testing the final product in the development environment
    - Consider multiple peer reviews, for instance, an internal one with the developers who worked on a larger feature together, and a following review with anyone interested from the larger team
- Demo
    - The original developer should now demo their work in the development environment to product owners 
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
    - Once the changes look good in development we can release to Test
    - We will ask developers to confirm that their features are aviable in Test
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
