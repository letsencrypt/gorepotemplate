# gorepotemplate

This repository serves as a template for other small go projects started by the
Let's Encrypt team. You should replace this title and description with one
appropriate to your project.

## Usage

This section should describe how to use your project. Here's how to use this
template repo:

1. Navigate to https://github.com/letsencrypt/gorepotemplate
2. Click "Use this template" and select "Create a new repository"
3. Select "letsencrypt" as the Owner of the repo, give it a good name, and
   create it
5. Set up the correct [general settings](settings):
   - Under Features, only select "Issues" and "Preserve this repository"
   - Under Pull Requests, only select "Allow squash merging", and set the commit
     message to "Pull request title and description"
   - Select "Automatically delete head branches"
6. Set up the correct [team access](settings/teams):
   - Grant both the Boulder Developers and Ops teams "write" permission
7. Set up the correct [rulesets](settings/rules):
   - Create a "New branch ruleset"
   - Name it "Protect main", and set the target branches to "Include default
     branch"
   - Restrict creation, restrict deletion, require linear history, and block
     force pushes
   - Require a pull request before merging, with 1 required approval, dismissing
     stale approvals, requiring review from Code Owners, and requiring approval
     of the most recent reviewable push
   - Only allow the Squash merge method
   - Require status checks to pass, and add the "test" job as a required check.
8. Create a PR updating this README file, and you're done!
   - Optionally: also update the CODEOWNERS file to represent what team will own
     this code.

## Contributing

This section should describe how to set up a development environment, make
changes, and run tests.
