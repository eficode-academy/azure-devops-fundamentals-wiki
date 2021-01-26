
# Task: Implement feature toggling
1. Create a new `FeatureToggles` class that reads an environment variable `WORKING`. 

    <details>
      <summary>Hint</summary>

    1. Add a `FeatureToggle.java` file next to `Main.java` with the content:
    ```
    package com.example;

    class FeatureToggle {
      public static boolean getWorkingFlag() {
        return System.getenv("WORKING") != null;
      }
    }
    ```
    </details>

2. Modify the `Main.index` method to print “Working…” if the toggle is on.

    <details>
      <summary>Hint</summary>

    1. Modify the `Main.index` method to this:
    ```
      public String index() {
        if (FeatureToggle.getWorkingFlag())
          return "Working...";
        else
          return "Running...";
      }
    ```
    </details>

# Task: Switch release trigger to automatic
1. Now we can safely set our Deploy pipeline to trigger automatically after the slowtest pipeline completes. Make this change. 
2. Deploy the code. 
3. Then inform the product owner (the trainer) that they can release the feature in production.