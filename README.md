# Daml Fundamentals Certificate Sample App

## Guess the number

This collection of contracts implements a "Guess the Number" game in DAML

There are three types of parties:
* Game Master: This party records their secret number on the ledger and invites players to participate.
* Public observer: The public observer can see all games that are currently going on, but not the secret numbers
* Players: Players are invited parties who can submit a single guess which the game master can compare against the secret.

### Starting the game

The game master creates a `Secret` contract and a `GuessingGame` contract which refers to it.

### Inviting players

The game master produces `GameInvitation` contracts for all the parties it wishes to invite to play the game.

Players can decline the invitation or make a guess by exercising `RejectInvitation` or `MakeGuess`, respectively.

### Determining a winner

The game master processes `GamePlayerGuess` contracts by submitting them for comparison against the secret. If a
guess is correct, the game automatically ends and a `GuessingGameResult` contract records the winner and the secret number.
The result contract is signed by both the winner and the game master.


## Building
To compile the project
```
$ daml build
```

### Testing
To test all scripts:
Either run the pre-written script in the `Test.daml` under /daml OR run:
```
$ daml start
```

### Running
To load the project into the sandbox and start navigator:
```
$ daml start
```
