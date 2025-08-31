REINFORCEMENT LEARNING BASED SOLUTION FOR SOLVING A SUDOKU

In this notebook we aim to solve a sudoku puzzle using a deep Q-Learning agent who finds an optimal position and the number to place in the position

Reward Shaping:

  Correct placement → +100 reward
  Completing rows/columns/boxes → incremental rewards (+4 for rows/columns, +8 for boxes)
  Penalties for conflicts and unnecessary steps → encourages efficiency and accuracy.

State Representation:

  Sudoku grid flattened to 81-length vector; CNN layers capture spatial relationships.
  Original grid stored to visualize changes and highlight agent decisions.

Action Space:

  81 positions × 9 possible numbers = 729 discrete actions.
  Action is split into position + number via divmod. Intention behind this is to allow the agent to choose both an optimal position and the right number for the position to make future desicions easier.

Training Strategy:

  Multi-attempt approach: agent retries puzzles to improve learning.
  Epsilon-greedy policy gradually reduces exploration.
  Experience replay (batch size 64) stabilizes learning.

Observed Results

  The agent gradually learns correct placements and can complete easier puzzles after repeated attempts.
  Green highlights show cells updated by the agent in real-time, illustrating decision-making.

Learning Dynamics:

  Early steps often penalized due to conflicts.
  Total reward increases with correct placements and puzzle completions over attempts.
  Epsilon decay reduces random actions, improving convergence.

Challenges / Limitations:

  High-dimensional action space (729 actions) increases training complexity.
  Puzzle completion is stochastic; agent may need multiple attempts per puzzle.
  Training convergence can be slow for harder Sudoku puzzles due to sparse rewards.

Future Improvements:

  Use Double DQN or Dueling DQN for more stable learning.
  Incorporate curriculum learning: start with simpler puzzles, gradually increase difficulty.
  Optimize CNN architecture to reduce overfitting and improve generalization across unseen puzzles.
