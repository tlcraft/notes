# Quality

Here are notes on building quality into software. From processes to bug ticket creation.

## Software Development Life Cycle

To help ensure a high level of quality, testing needs to be done at all levels throughout development and the release process. Here’s an overview of the areas where testing should occur.

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
- Test Env Regression Testing
- UAT
- Deploy to Production
