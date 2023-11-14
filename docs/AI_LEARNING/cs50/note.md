# CS50 : Artificial Intelligence with Python
## [Week 0](https://cs50.harvard.edu/ai/2020/weeks/0/)
### [Search](https://cs50.harvard.edu/ai/2020/weeks/0/#search)
Finding a solution to a problem, like a navigator app that finds the best route from your origin to the destination, or like playing a game and figuring out the next move.  
Search problems involve an agent that is given an initial state and a goal state, and it returns a solution of how to get from the former to the latter. A navigator app uses a typical search process, where the agent (the thinking part of the program) receives as input your current location and your desired destination, and, based on a search algorithm, returns a suggested path. However, there are many other forms of search problems, like puzzles or mazes.  
#### Agent
an agent is an entity that perceives its environment through sensors and acts upon that environment through actuators.
#### State
A state is a configuration of the agent and its environment.
initial state : the state in which the agent begins
goal state : the state which the agent wants to reach
#### Action
An action is a choice that can be made in a state.
Action(s) : returns the set of actions that can be executed in the given state
#### Transition Model
A description of what state results from performing any applicable action in any state.
Result(s, a) : returns the state resulting from performing action a in state s
#### state space
The set of all states reachable from the initial state by any sequence of actions.
#### Goal Test
A way to determine whether a given state is a goal state.
GoalTest(s) : returns true if s is a goal state
#### Path Cost
A numerical cost associated with a given path.
#### optimal solution
A solution that has the lowest path cost among all solutions.
#### node 
A data structure that keeps track of:
- a state
- a parent (node that generated this node)
- an action (action applied to parent to get node)
- a path cost (from initial state to node)
- depth (of the node in the search tree)
#### Approach
Start with a frontier that contains the initial state.
Repeat:
- If the frontier is empty, then no solution.
- Remove a node from the frontier.
- If node contains goal state, return the solution.
- Expand node, add resulting nodes to the frontier.
#### Revised Approach
Start with a frontier that contains the initial state.
Start with an empty explored set.
Repeat:
- If the frontier is empty, then no solution.
- Remove a node from the frontier.
- If node contains goal state, return the solution.
- Add the node to the explored set.
- Expand node, add resulting nodes to the frontier if they aren't already in the frontier or the explored set.
- Expand node, add resulting nodes to the frontier if they aren't already in the frontier or the explored set.

#### depth-first search
- uses a stack as its frontier
- expands the deepest node in the frontier
- implementation: frontier = Stack(), explored = Set()
- complete: yes, if finite state space, no if infinite state space
- time complexity: O(b^m), b is branching factor, m is max depth of state space
- space complexity: O(bm)

#### breadth-first search
- uses a queue as its frontier
- expands the shallowest node in the frontier
- implementation: frontier = Queue(), explored = Set()
- complete: yes, if finite state space, no if infinite state space
- time complexity: O(b^d), b is branching factor, d is depth of goal state
- space complexity: O(b^d)
- optimal: yes, if cost = 1 per step

#### uninformed search
- uses no problem-specific knowledge

#### informed search
search strategy that uses problem-specific knowledge to find solutions more efficiently
- greedy best-first search
> search strategy that expands the node that is closest to the goal, as estimated by a heuristic function h(n)
A* search
> search strategy that expands node with lowest value of g(n) + h(n)    
> g(n) = cost to reach node  
> h(n) = estimated cost to goal  
It is optimal if h(n) is admissible (never overestimates the true cost) and consistent (for every node n and successor n' with step cost c, h(n) <= h(n') + c)
  

#### multy agent search
**minimax**
> algorithm for finding optimal move in a two-player, zero-sum game
> - zero-sum game: one player's gain is another player's loss
> - optimal strategy for one player is the worst-case scenario for the other
> - minimax algorithm assumes that opponent plays optimally

#### GAME
- S0
> initial state
- player(s)
> return which player has the move in state s
- actions(s)
> return set of legal moves in state s
- result(s, a)
> return state after action a taken in state s
- terminal-test(s)
> return true if state s is terminal
- utility(s)
- return final numerical value for terminal state s

using struct of tree to represent the game tree can make it easier to implement minimax algorithm

#### tic-tac-toe
- state: 9 squares, X or O or empty
- action: placing X or O in an empty square
- terminal test: 3 in a row, or no empty squares
- utility: +1, -1, 0
- optimal strategy: play perfectly
- complexity: 9! = 362880
```python
function Max-Value(s): 
    if Terminal(s)
        return Utility(s)
    v = 负无穷
    for action in Actions(s):
            v = Max(v,Min-Value(Result(s,action)))
    return v
function Min-Value(s): 
    if Terminal(s)
        return Utility(s)
    v = 正无穷
    for action in Actions(s):
            v = Min(v,Mas-Value(Result(s,action)))
    return v

```
optimization: alpha-beta pruning
> - alpha: the value of the best (i.e., highest-value) choice we have found so far at any choice point along the path for MAX
> - beta: the value of the best (i.e., lowest-value) choice we have found so far at any choice point along the path for MIN
```python
    function Max-Value(s, alpha, beta): 
        if Terminal(s)
            return Utility(s)
        v = 负无穷
        for action in Actions(s):
                v = Max(v,Min-Value(Result(s,action), alpha, beta))
                if v >= beta:
                    return v
                alpha = Max(alpha, v)
        return v
```

#### depth-limited minimax
- depth-limited minimax: minimax algorithm that cuts off search at a given depth
- evaluation function: an estimate of the expected utility from a given state
- horizon effect: when a search algorithm fails to look ahead far enough
- quiescence search: a search algorithm that continues to search until a quiet position is reached
- iterative deepening: an algorithm that performs a series of depth-limited searches, increasing the depth limit with each iteration

**evaluation function**
- evaluation function: an estimate of the expected utility from a given state
- static evaluation function: an evaluation function that always returns the same value for a given state
- heuristic evaluation function: an evaluation function that estimates the expected utility from a given state
- material advantage: the difference in material between two players in a game
- mobility: the number of legal moves available to a player in a game
- potential mobility: the number of legal moves available to a player's pieces in a game
- center control: the number of squares in the center controlled by a player in a game
- pawn structure: the arrangement of a player's pawns in a game
- piece-square tables: a table of values for each piece at each square on the board
- opening book: a database of expert moves in the opening stage of a game



