
# Getting an overview

Before we start doing anything it is nice to get an overview of the current
state of devops metrics in your new team.

Therefore we will try to answer the following questions:

<details>
  <summary>Hint</summary>

  Not all of the  questions below can be answered with queries alone.
</details>

----------

1. What is our deployment frequency? How often do we deploy?

    <details>
      <summary>Hint</summary>

    There is a ticket for every time we have deployed.
    </details>

2. What is our lead time?

    <details>
      <summary>Hint</summary>

    Create a query to show the columns `Created Date`, and `State Change Date`
    or `Closed Date` for tickets that are `Done done`.
    </details>

3. What is our change failure rate? How many tickets have been `Done done`, but
   are not currently in that state?

    <details>
      <summary>Hint</summary>

    There is a query operator called "Was Ever".
    </details>

4. What is our mean time to recovery? How long is it since the tickets from
   question 3. were `Done done`?

   We don't actually have any "recovered" items in the project, so the best we
   can do is get an esitmate or lower bound by looking at the tickets from Q3
   and investigate how long it has taken so far to not fix them yet.

    <details>
      <summary>Hint</summary>

    Open them and examine their history to find out when they were first `Done done`
    and when they were.
    </details>

# Finding work

Having gotten our bearings it is time to start being productive:

- Discuss what PBI you should work on?
