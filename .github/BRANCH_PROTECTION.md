# Branch Protection Rules for Octokeep

This document describes the branch protection rules that should be configured for the `main` branch.

## Main Branch Protection Settings

The following settings should be enabled for the `main` branch in the GitHub repository settings:

### Required Reviews
- ✅ Require pull request reviews before merging
- ✅ Required approving reviews: 1
- ✅ Dismiss stale pull request approvals when new commits are pushed

### Status Checks
- ✅ Require status checks to pass before merging
- ✅ Require branches to be up to date before merging
- Required status checks:
  - `branch-protection-check` (from branch-protection.yml workflow)

### Additional Settings
- ✅ Require conversation resolution before merging
- ✅ Require linear history
- ✅ Include administrators (enforce rules for admins)
- ✅ Restrict who can push to matching branches
- ✅ Allow force pushes: **Disabled**
- ✅ Allow deletions: **Disabled**

## How to Configure

To configure these settings in GitHub:

1. Go to your repository on GitHub
2. Click on **Settings** → **Branches**
3. Under "Branch protection rules", click **Add rule**
4. In "Branch name pattern", enter: `main`
5. Enable the checkboxes as listed above
6. Click **Create** or **Save changes**

## Automated Enforcement

The `.github/workflows/branch-protection.yml` workflow provides automated checks to ensure:
- All changes to main go through pull requests
- Status checks are run on all PRs
- Code review requirements are enforced

## CODEOWNERS

The `.github/CODEOWNERS` file automatically requests reviews from designated code owners when PRs are opened, ensuring proper oversight of changes.

## Benefits

These protection rules ensure:
- Code quality through peer review
- Prevention of accidental direct pushes to main
- Consistent commit history
- Required passing tests before merge
- Proper tracking of all changes
