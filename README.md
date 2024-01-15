
This project involves creating a Rock-Paper-Scissors (RPS) game server in Rust using async-await syntax and async-std. Learned handling asynchronous operations, managing tasks concurrently, and implementing a game logic system.

## Async Function: `play_command`
The `play_command` function manages the flow of a game round, handling player interactions, weapon selection, and outcome determination. It utilizes asynchronous features to coordinate between players and ensures a smooth gameplay experience.

### Key Aspects:
- Asynchronous communication with peers using `async-await` syntax.
- Utilization of channels (`channel::Sender`) for inter-task communication.
- Handling timeouts (`play_timeout` and `weapon_timeout`) for responsive gameplay.

## Async Function: `weapon_loop`
The `weapon_loop` function allows a player to choose their weapon within a specified timeout. It captures user input, validates it, and returns the selected weapon or `None` if the timeout occurs.

### Key Aspects:
- Asynchronous user input handling for weapon selection.
- Timeout management to ensure responsive user interactions.
- Utilization of a loop for continuous user prompts until a valid input or timeout.

## Async Function: `play_matchmaker_task`
The `play_matchmaker_task` function acts as a matchmaker, pairing players for RPS matches. It listens for play requests, manages timeouts, and initiates referee tasks for matched players.

### Key Aspects:
- Utilization of asynchronous channels (`channel::Receiver`) for receiving play requests.
- Timeout handling for matchmaking to prevent indefinite waiting.
- Dynamic task creation (`task::Builder`) for referee tasks.

## Async Function: `referee_task`
The `referee_task` function orchestrates a single RPS match between two players. It coordinates the exchange of weapons, determines the outcome, updates game statistics, and communicates results to players.

### Key Aspects:
- Use of `oneshot::Sender` for bidirectional communication between referee and players.
- Graceful handling of player disconnections during different phases of the match.
- Statistical updates to a shared database (`DataBase`) for game outcomes.

