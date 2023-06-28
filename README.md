# Flyway Demo

Getting Started: https://documentation.red-gate.com/fd/quickstart-how-flyway-works-184127223.html

---

This repository has some codes sketches I did while learning more about Flyway

## My Testing Scenario

## Evaluation Criteria
Since I'm evaluating Flyway against other similar tools I have come up with a couple of features to take into consideration. Hopefully I'll have a good idea about each of them after following this project through to the end.

### POC Complexity
*how difficult is it to build a working demo*

### Cost
*What I can and cannot do with the free plans*

### SQL Server Compatibility

### Impact on Developer Workflow
*How transparent will the transition be, from not knowing a new tool is being used in the pipeline to having to learn a brand new tool*

### Integration with Existing Databases
*How well can I take an existing, populated database and start using Flyway?*
- https://documentation.red-gate.com/fd/baselining-your-downstream-environments-146211067.html
- https://www.red-gate.com/hub/university/courses/flyway/flyway-desktop-enterprise-implementation/concepts/schema-model

- Schema Model: The directory and file structures with all the create scripts necessary to keep the database in its current state
- You can pretty quickly wire up Flyway to an existing database and generate a Schema Model with differente file types separated by folder
  - For every object in the database, there will be a separate file in the schema model
- Baseline Script: Script that captures everything that currently exists in a production like environment so Flyway knows what to change
- Filters are important to create the baseline script, because there are some objects in production that shouldn't be versioned
- Changes in the schema model need to be converted to migrations using a **shadow database**, which is an ephemeral copy of the development database that will be recreated from scratch using only the migration scripts
  - Good practice is to have at least 1 shadow database for each developer actively working in the team
  - Need to see if these shadow databases can be hosted locally for each developer to reduce costs

### Documentation
*How well is the project documented*

### Support
*Taking into consideration if the tool is still currently maintained and supported, and how much longer this support will last*

### Rollback
*How easy is it to rollback changes once they are commited*

### Reuse of Existing SQL Scripts
*How well can I reuse my existing SQL scripts repository*
- The SQL Scripts that currently exist are technically my schema model, so it can probably be reused pretty well
- That being said, there might be some small adjustments regarding multiple objects created by the same script, for example

### Maintenance of Integration
*How much has to be set up in order for CI/CD to work and how fragile is it*