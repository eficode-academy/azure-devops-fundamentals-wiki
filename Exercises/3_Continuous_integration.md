
# Task: Automatic Compile
1. Create a pipeline to build the code with gradle. 

    <details>
      <summary>Step by step</summary>

    1. Create a file called `ci.yml` containing this minimal pipeline:
        ```
        trigger:
          - *

        pool:
          vmImage: "ubuntu-latest"

        steps:
          - script: |
              echo “Hello, World!”
            displayName: "Print important message"
        ```
    2. Use this step to checkout the code:
        ```
        - checkout: self
        ```
    2. Use this step to run gradle:
        ```
        - task: Gradle@2
          inputs:
            workingDirectory: ""
            gradleWrapperFile: "gradlew"
            gradleOptions: "-Xmx3072m"
            javaHomeOption: "JDKVersion"
            jdkVersionOption: "1.8"
            jdkArchitectureOption: "x64"
            publishJUnitResults: true
            testResultsFiles: "**/TEST-*.xml"
            tasks: "build"
        ```
    3. Go to Pipelines.
    4. Click "New pipeline".
    5. Click "Azure Repos Git (YAML)".
    6. Select the correct repo.
    7. Click "Existing Azure Pipeline YAML file".
    8. Select the YAML file, then "Continue".
    9.  Click the down-arrow next to "Run" and hit "Save".
    10. Click the three dots in the upper right, and hit "Rename/move".
    11. Call it "ci".
    </details>

2. It should trigger on pushes to all branches, except main. 

    <details>
      <summary>Hint</summary>

    ```
    trigger:
      branches:
        exclude:
          - main
    ```
    </details>

3. Also set it to timeout after 5 minutes.

    <details>
      <summary>Hint</summary>

    ```
    jobs:
      - job: Test
        timeoutInMinutes: 5
    ```

    Important: `steps` needs to be indented to the same level as `timeoutInMinutes`.
    </details>

# Task: Automatic integration
1. First, we need to setup the permissions in the project settings:
   ![](settings.png)
2. Setup a new pipeline to automatically merge a branch into main. 

    <details>
      <summary>Git commands</summary>

    ```
    git rebase origin/main
    git branch main
    git push origin main:main
    git push origin :$(Build.SourceBranch)
    ```
    </details>

    <details>
      <summary>Hint</summary>

    ```
    - checkout: self
      persistCredentials: true
    ```
    </details>

3. It should trigger automatically after the CI build but only on `ready/*` branches. 

    <details>
      <summary>Hint</summary>

    ```
    trigger: none
    resources:
      pipelines:
        - pipeline: name
          source: ci
          trigger:
            branches:
              - ready/*
    ```
    </details>

4. Remember to update the "How to contribute" section in the `README.md`.
5. Test it by pushing a commit to a `ready/` branch.

    <details>
      <summary>Hint</summary>

    ```
    git push origin HEAD:ready/[BRANCH]
    ```
    </details>

# Task: Safer integration
Add fast tests to the CI build.

<details>
  <summary>Hint</summary>

In the `ci.yml` change
```
tasks: "build"
```
into
```
tasks: "test"
```
</details>
