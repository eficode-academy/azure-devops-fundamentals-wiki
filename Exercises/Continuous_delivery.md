
# Task: Set up a slow pipeline
Setup a new pipeline to automatically run the slowtest gradle task when something is pushed to main.

<details>
  <summary>Step-by-step guide</summary>

1. Let’s start by cloning the CI pipeline.
2. Rename the pipeline, and change the default parameter as we did earlier.
3. Go into “Triggers” and change “Exclude” to “Include”.
4. Also go into “Options” and change the timeout to 30 minutes.
5. Test it by pushing a commit with:
```
git push origin [BRANCH]:ready/[BRANCH]
```
</details>

# Task: Set up a release pipeline (manually triggered)
Setup an automatic deployment pipeline. Use variables to store the app name and Access Token.

<details>
  <summary>Hint</summary>

Instructions on how to deploy can be found in the repo `README.md`.
</details>

<details>
  <summary>Step-by-step guide</summary>

1. Create an empty pipeline like we did earlier, and name it “Deploy”.
2. Add a “Command Line” task with the Git commands above.
3. Go to the “Variables” and add “AppName” and “PAT” from Heroku.
4. Test it by querying the pipeline and going to your [AppName].herokuapp.com.
</details>

