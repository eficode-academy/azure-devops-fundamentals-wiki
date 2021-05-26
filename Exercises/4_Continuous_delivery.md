
# Task: Set up a slow pipeline

Setup a new pipeline to automatically run the slowtest gradle task when something
is pushed to `main`. It should have a timeout of 30 minutes. Test it.

# Task: Set up a release pipeline (manually triggered)

1. Setup an automatic deployment pipeline. 
    <details>
      <summary>Hint</summary>

    Instructions on how to deploy can be found in the repo `README.md`.
    </details>
2. Use variables to store the app name and Access Token.
    <details>
      <summary>Hint</summary>

    ```yaml
    variables:
      - name: "AppName"
        value: ""
      - name: "PAT"
        value: ""
        readonly: true
    ```

    </details>
3. Test it by running the pipeline and going to your `[AppName].herokuapp.com`.
