# New Project Checklist

- [ ] Clone https://github.com/letsencrypt/gorepotemplate
- [ ] Copy the `gorepotemplate` folder to a new project folder (`cp -r gorepotemplate <project name>`)
- [ ] Change into the new project folder (`cd <project name>`)
- [ ] Delete the existing `.git` folder from the template project (`rm -rf .git`)
- [ ] Initialize a new git repo (`git init`)
- [ ] Create the Github repoistory in the web UI. Do not select a project language for a `.gitignore`, or a license (these are included in `gorepotemplate`)
- [ ] Add the Github repository as a git remote (`git remote add origin git@github.com:letsencrypt/<project name>.git`)
- [ ] Disable unneeded Github repository features at `https://github.com/letsencrypt/<projectname>/settings` (e.g. disable Wikis, Projects, etc as appropriate)
- [ ] Configure "Team" collaborator access at `https://github.com/letsencrypt/<projectname>/settings/collaboration` to add dev/SRE teams
- [ ] Enable Travis
- [ ] Enable Coveralls
- [ ] Enable Golang CI (optional)
- [ ] Configure branch protection rules at `https://github.com/letsencrypt/<projectname>/settings/branches`
- [ ] Mark the checklist complete script executable (`chmod +x checklist.complete.sh`)
- [ ] Run `./checklist.complete.sh`

# Enabling Travis CI:

Visit https://travis-ci.org/ (not `.com`, the letsencrypt org is still on the
legacy Travis). Under https://travis-ci.org/account/repositories click the Let's
Encrypt organization and then enable the new repository in "Legacy Services
Integration". You may have to click "sync account" if the repo was created
recently.

Under the project settings
`https://travis-ci.org/letsencrypt/<projectname>/settings` you may want to
enable a "cron jobs" build of master on a daily interval that always runs. This
helps prevent bitrot when there are not many new commits.

## Enabling GolangCI (optional)

1. Log in with github to https://golangci.com/
1. Visit https://golangci.com/repos/github
1. Add the project repo.
1. You may want to ensure the Golang CI status check isn't required to merge
   PRs. The `.travis.yml` that comes in this repo already runs `golangci-lint`
   in Travis and so the Github integration is a nice-to-have.

## Enable Coveralls:

1. Log in with github to https://coveralls.io/
1. Add the project repo under https://coveralls.io/repos/new
1. That's it! You don't have to fiddle with a `repo_token` if the repo is
   public.

## Github Branch protection recommendations:

In the Github branch protection UI configure a branch protection rule for master
that has the following enabled:

* Require pull request reviews before merging
  * Dismiss stale pull request approvals when new commits are pushed
* Require status checks to pass before merging
  * Require branches to be up to date before merging
  * Travis CI status check required
* Include administrators
