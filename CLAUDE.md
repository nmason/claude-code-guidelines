# Project Guidelines

## Critical: Specification-First Approach

**Before starting ANY task (planning, development, bug fixes, new features), you MUST:**

1. **Read `docs/specification.md`** - Understand the full project context and requirements
2. **Work in accordance with the specification** - All work must align with the documented specification
3. **Update the specification** when adding new features or making architectural changes

## Specification Documents
**Current Phase:** Specification Complete (v1.2)

**Codename:** Planner

**What it is:** A rostering tool for retail, hospitality, churches, and clubs to create staff/volunteer rosters. Solves the problem of time-consuming availability collection and roster juggling.

- **`docs/specification.md`** - The complete project specification. This is the source of truth for what the project is and how it should work.
- **`docs/specification-changelog.md`** - Tracks all changes to the specification. Every modification to the specification must be logged here with:
  - Date of change
  - Brief title describing the change
  - Details of what was added, removed, or modified
- **`docs/technology.md`** - Technology stack documentation including syntax examples, package usage, and configuration notes. Reference this for implementation details.
- **`docs/brainstorm.md`** - Working document for capturing ideas during planning. Uses a temperature rating system (1-5) to track likelihood of inclusion. Temperature 5 ideas get promoted to the specification.
- ** docs/linear-issues.md ** - A reference to all linear tasks for this project.  Keep this document up to date, when you complete a task, ensure it's checked off.  If you create/modify/delete a issue, ensure document is updated.  When viewing milestones or phases, this is your reference sheet to easily find the issue rather than relying on the Linear MCP, which is an alternative but slower method.


## Workflow

1. Read the specification before beginning work
2. Ensure your task aligns with the specification
3. If the task requires specification changes, update both the specification and changelog
4. Branch out from `development` branch into a new branch according to linear suggest git branch name
5. Complete the task in accordance with the specification
6. Ensure tests are created with a high code coverage
7. Ensure Acceptance Criteria is meet
8. Follow Git Workflow and Git Acceptance Criteria

## Git Workflow and Git Acceptance Criteria
**Important:** All work should be done on feature branches and submitted via Pull Requests. Do not push directly to the production branch.
1. Commit often, each mini task within issue should be committed to create branch snapshots.
2. Every issue should be worked on it's own seperate branch, as per `workflow` point 4 above.
3. When issue is completed, create a PR using github cli
4. Ensure all github actions pass.  Review and fix any failing actions and recommit.  Recheck and repeat until all actions pass (while meeting acceptance criteria).
5. Perform a code review using `review` skill.  Post full review as a PR Comment.
6. Review review points.  For any review points where can justify for not doing, create a PR comment with justification.  Fix any unjustified points from the review.  Re-review including your justifications until the review is satisfied.
7. When all Actions pass, review is satisfied you can merge branch into `development`.
8. Checkout and pull development ready for the next issue.


## Technology Notes

- **Wayfinder (dev-next):** This project uses the public beta of Laravel Wayfinder. Refer to `docs/technology.md` for usage patterns. The API may change before v1.0.0 - check documentation if encountering issues.
- **Laravel Boost:** MCP server is available for AI assistance and foundation rule guidelines. Use `php artisan boost:mcp` for enhanced context awareness.

# Key Architectural Notes

### Controllers
Use actions where possible, keep controllers lean.

### Actions
We prefer to utilise Action classes to provide specific verb logic for a certain action rather than keeping our verb logic in a controller.  This allows us to share the action between other controllers easily, keep our controllers skinny and also allows more testibility.

### Services
We prefer Actions where a piece of logic has one Responsibilities and Services over logic that has multple responsibilities or shared inheritance (such as a API wrapper)

## PHP Stan
we use phpstan on level 10, any changes will need to be compliant with any work requiring a passing result when running `composer phpstan`.  Work cannot be considered complete unless phpstan passes.

## Pest Testing
We utilise Pest for our testing framework. We should test not just unit / features tests but also browser tests utilizing Pest.  We should run pest in parallel.  Testing coverage is important, and we should maintain a high level of test coverage.



===
