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
- Demo
- Dev Env Regression Testing
- Test Env Regression Testing
- UAT
- Deploy to Production
