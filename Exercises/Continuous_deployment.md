
# Task: Implement feature toggling
Create a new FeatureToggles class that reads an environment variable “WORKING”. Modify the Main.index method to print “Working…” if the toggle is on.

<details>
  <summary>Step-by-step guide</summary>

1. Add a “FeatureToggle.java” file next to “Main.java” with the content:
```
package com.example;

class FeatureToggle {
  public static boolean getWorkingFlag() {
    return System.getenv("WORKING") != null;
  }
}
```
3. Modify the Main.index method to this:
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
Now we can safely set the “Deploy” pipeline to trigger after the slowtest pipeline completes. After the code is deployed try flipping the toggle with the commands:
```
heroku config:set WORKING=true
heroku config:unset WORKING
```