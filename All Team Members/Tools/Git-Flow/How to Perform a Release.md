# How to Conduct a Git-Flow Release
	
## asdf

This release workflow is specific to git repositories hosted on GitHub that are enabled for a git-flow branching model on the local version of the repo. The process his involves creating a local release branch, pushing up to git, closing and back merging all git flow commits to branch.

The release process checklist is broken into four phases:

- Release definition and preparation
- Pre-release work completion
- Release
- Deployment

Note there is a Glossary of terminology at the end of this document.

## Documentation of Release

When performing a release, post in the appropriate Slack channel and workspace informing relevant members of relevant teams of the start of the release process. As you walk through each step of this document, you'll update the Slack in a thread on that post with relevant informations and the steps you're taking.

Something like this:

![Example of Slack Release Thread](https://d.pr/i/xxAtgE+)


## Release definition and preparation
These steps can and should happen as early as possible, as soon as a set of features emerges as likely for the next release.

- Determine roles for the release
	1. Product manager:
		- Be point of contact for site owner / client
		- Call the feature freeze
		- Green light deployment to production
		- Review / confirm / update roles and make sure they’re clear.
	2. Release Owner:
		- Point of contact for dev team
		- Call the feature freeze
		- Complete this checklist; shepherd code through the release

## Call the feature freeze
The feature freeze is intended to prevent conflicts or complications with deployment. It should be planned in advance, and coordinated with all developers commiting to the relevant repository(ies).

- **Who**:  The product manager, with release owner’s approval and the dev team’s collective input
- **What**: When a project is in "feature freeze", nothing should be landed to `develop`.
- **How**: Announce branch/feature freeze in Slack with an @channel or @here announcement

![Output to Slack](https://d.pr/i/aP7dRV+)

This output should be included in the Slack release thread, and output to main channel for maximum visibility.
		
## Pre-release work completion
Leading up to the release, complete the included features and bugfixes, finish QA, and get final approval to proceed.

- Development work complete
	- Who: Dev team
	- What: This is complete when work is submitted for internal review
- Testing on `develop` passing QA
	- Who: Product manager and developers involved in tasks under review
	- What: This includes fixes as needed to resolve issues uncovered during QA
- Product manager gives approval to proceed
	- Who: Product manager, in communication with the client

![Output to Slack](https://d.pr/i/iBZbFx+)


## Release
Create the actual release.

- Create the changelog in IA Writer or another markdown tool, example here (better example coming/John),  There is also and example snippet in Alfred entitled 'release changelog'
	- Who: Release manager
	- What: Plain-English notes describing new features, fixes, and other changes introduced by the release. More details here.
	- When: After a feature freeze, this can proceed even before all tasks included in the feature are complete.
- Ensure your local Git repository and the remote repository are synchronized
	- Who: Release manager
	- What: `git fetch --all` or git pull or git push
- Ensure your local `develop` branch is synchronized with the origin remote’s `develop`
	- Who: Release manager
	- What: `git checkout develop && git pull && git push`
- Confirm all branches for included features and fixes are landed on `develop`
	- Who: Release manager
	- What: Compare `develop` commit graph with features & fixes included in release notes
Confirm `develop` is passing QA on the Staging instance
- Who: Product manager
- What: Confirmation of a go-ahead to deploy (verbal or written, whichever is appropriate given communication systems in use)
- Create a "release" branch and a pull request, finish, publish, and back-merge it. Instructions below
	- Who: Release manager
	- What: Create and publish the release in Git
		- Use Semantic Versioning to increment major, minor, or build numbers as appropriate, depending on the contents of the release.
		- Increment version numbers — see VERSION file in project root
		- In PR description, include release changelog
		- In PR description, cross-link the PR and the task object or discussion (e.g. in Trello, Slack,etc.)
		- The commit message will need to be given to git three times, once for the merge to `master`, once for the tag, and once for the back-merge to `develop` 
	- How:  
		- `git flow release start v<release num>` (from develop)  
		- `git flow release publish v<release num>` (publishes to remote)
	- Navigate to Github repository and open a pull request for the branch
		- Navigate to relevant GitHub repository
		- Click release branch
		- Press button to create new PR
		- Compare against master
		- In PR description paste the changelog
		- click Create PR
		- Merge the PR on GitHub
			- Announce that you've landed the PR per git-flow best practice:
			![Output to Slack](https://d.pr/i/EZPPkM+) 
		- Confirm Merge PR develop to master (mergers the release remotely)
	- Draft commit message including the release’s “summary” text and changelog, the task URL (if any), and the PR URL
	- `git flow release finish -F v<version>`
copy and past changelog to commit
	- `git checkout master && git push master && git push --tags && git checkout develop && git push develop`
run git push –tags to confirm tags are recorded remotely
- Create a Github “release” object from the tag
	- Who: release manager
	- How:
		- Navigate to Github repository releases at `https://github.com/[ORGNAME]/[REPONAME]/releases`
		- Click draft a new release
		- Select tag 
		- Select target is master
		- Name should be Version release number
		- Paste in changelog to description
		- Click publish release
		- In release description, include release changelog
		- In release description, cross-link the the task object or discussion (e.g. in Trello, Slack,etc.)

- Announce release is complete
	- Who: release manager
	- How: In whatever communication medium the team is using. (e.g. @channel/@here announcement in Slack). If a written medium, link to the release on Github.

![Output to Slack](https://d.pr/i/XNK6yk+)

## Deployment
Deploy the release to production, to take the changes live, and do post-deploy QA.

- QA production
	- Who: product manager, potentially with the release manager and developers involved in included tasks
	- What: Thorough QA of production to confirm the release’s changes applied without issues.

## Glossary
**Feature Freeze**
Calling a feature freeze can be used to avoid scope-creep and pile-on, and thus give clearance for the team to finish the few things that may still be left.

When a project is in "feature freeze", nothing should be landed to `develop` without clearing it with the Release owner. This does not mean that everything has to be landed yet. If there are pending items slated for the release, just make sure that’s clear to everyone.

Hotfixes may interrupt a feature freeze. If a hotfix lands during a freeze, be sure to account for it in testing. A freeze cannot block a hotfix/ branch from being back-merged into `develop`.

**Release**
A software release is a group of changes packaged together as a single point in the history of the codebase. Typically releases have a primary theme or focus, although this is not required. Releases are always a stable point for deployment (in other words, they cannot include works in progress, or critical bugs known to exist at the time of the release), should a roll-back or a deployment to a brand new instance be necessary.

**Release Notes**
Release notes document the contents of a release in plain-english. This is especially useful for non-developer team members (such as the product manager), but is useful for developers, as well. Immediately upon completion of a release, release notes are useful for broadly communicating the change-sets to all stakeholders. Later in time, as the team’s focus switches to tasks and the memory of the release fades, the release notes will serve as a comprehensive yet concise historical record of how the code base has evolved.

Release notes should take the following form:

- A concise title summarizing the theme of the release in a single phrase
- The first sentence should be a complete sentence, comprehensively summarizing the contents of the release, grouping like tasks as is natural.
- A changelog, with a complete list of bulleted changes, broken into the following categories, in this order: “features”, then “fixes”, then “other”.
- The long-term storage location for releases is in the Github repository, using that service’s “Releases” features.

Examples of well-formed release notes:

v1.1.0 (typical/ '.../releases/tag/v1.1.0')
v1.2.1 (shorter than normal/'.../releases/tag/v1.2.1')