
# Getting an overview

Before we start doing anything it is nice to get an overview of the state of devops in your new team. Therefore we look up:

1. What is our deployment frequency? How often do we deploy?

    <details>
      <summary>Hint</summary>

    There is a ticket for every time we have deployed.
    </details>

2. What is our lead time?

    <details>
      <summary>Hint</summary>

    Create a query to show the columns `Created Date`, and `State Change Date` or `Closed Date` for tickets that are `Done done`.
    </details>

3. What is our change failure rate? How many tickets have been `Done done`, but are not currently?

    <details>
      <summary>Hint</summary>

    There is a query operator called "Was Ever".
    </details>

4. What is our mean time to recovery? How long is it since the tickets from 3. were `Done done`?

    <details>
      <summary>Hint</summary>

    Open them and examine their history to find out when they were first `Done done`.
    </details>


# Finding work

Having gotten our bearings it is time to start being productive:

- Discuss what PBI you should work on?


