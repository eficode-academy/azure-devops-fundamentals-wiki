
# Task: Automatic Compile
Create a pipeline to build the code with gradle. It should trigger on pushes to all branches, except main. Also set it to timeout after 5 minutes.

<details>
  <summary>Step-by-step guide</summary>

1. Navigate to “Pipelines” and click “New Pipeline”. Then “Use the classic editor”.
2. Hit “Continue”, as the default repo settings are correct.
Search for the “gradle” template, and apply it.
3. Set it to trigger automatically when pushing to any branch other than “main”
4. Test it
</details>

# Task: Automatic integration
Setup a new pipeline to automatically merge a branch into main. It should trigger automatically after the CI build but only on `ready/*` branches. 

First, though, we need to setup the permissions in the project settings:

<details>
  <summary>Hint: The git instructions are on the next page.</summary>

These are the necessary Git commands:
```
git rebase origin/main
git branch main
git push origin main:main
git push origin :$(Build.SourceBranch)
```
</details>

<details>
  <summary>Step-by-step guide</summary>

1. Create a new pipeline, and select the “Empty job”.
2. Add a new “Command Line” task, and put the git commands from above into the “Script” part.
3. Select the “Agent job” and under “Additional options” enable “Allow scripts to access OAuth token”
4. Under “Triggers” add a “Build completion” trigger, and select your “CI” job. Also set the branch filter so it only runs on `ready/*` branches.
5. Test it by pushing a commit with:
```
git push origin [BRANCH]:ready/[BRANCH]
```
6. Test it
</details>

# Task: Safer integration
Add fast tests to the CI build.

<details>
  <summary>Step-by-step guide</summary>

1. Navigate into the CI pipeline. Because the gradle template automatically takes a parameter for which argument to pass to gradle we can simply change the default value for this parameter. Select “Pipeline” and change “Tasks” to “test”.
2. Test it
</details>
