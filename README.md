# Assignment 1
|Std ID|Name|
|------|-|
|K22-8709|Mujtaba Junaid|
|K22-4049|Anas Soharwardy|

## Q1
Q1: Turing's Original Paper on AI (Turing, 1950):

•	Objections still carrying weight: 

The "Argument from Consciousness" and "Lady Lovelace's Objection" still carry weight. The debate on machine             consciousness persists, and AI systems are limited by their programming.

•	Refutations validity:

Turing's refutations are valid to some extent, acknowledging that machines can exhibit intelligent behavior without true understanding

•	New objections:

Ethical concerns, bias in AI algorithms, and job displacement are new objections arising from recent developments.

•	Turing Test prediction:

Turing's prediction of a 30% chance for a computer passing the Turing Test by 2000 appears optimistic, as of 2024, with no AI consistently passing the test indistinguishably from a human.

## Q2
Q2: Tasks Currently Solvable by Computers:
1.	Playing table tennis(ping pong): Yes, is quite evident that the computers can play at a high level.
2.	Driving in Karachi: Partially solvable; challenges include complex traffic and unpredictable human behavior.
3.	Playing bridge: Yes, computers can play at a competitive level.
4.	Discovering and proving new theorems: Limited; AI aids in theorem proving but doesn't replace human mathematicians.
5.	Writing an intentionally funny story: Partially solvable; AI-generated content exists, but true humor comprehension remains a challenge.
6.	Giving legal advice: Limited; AI can assist, but nuanced legal understanding requires human expertise.
7.	Translating spoken English to Urdu: Partially solvable; real-time translation is possible, but challenges remain in idiomatic expressions and context.


## Q3
Q3: Agent for a Familiar Domain:

•	Domain:

Online customer support chat for e-commerce.
    
•	Environment Characteristics:

Accessible: Yes.

Deterministic: No (customer queries are variable)

Episodic: Yes (each customer interaction is distinct)

Static: No (product availability and promotions change)

Continuous: No (distinct interactions)

•	Agent Architecture:

A hybrid architecture combining reactive elements (responding to common queries) and deliberative elements 
      (learning from customer interactions).


## Q4
Q4) PEAS Descriptions:

1.	Playing soccer:
   
    •	Performance: Score goals, prevent opponent goals.
  	
    •	Environment: Soccer field with players, goals, and a ball.
  	
    •	Actuators: Muscles, joints.
  	
    •	Sensors: Eyes, ears.
  	
2.	Exploring the subsurface of Arabian Sea:
   
    •	Performance: Map underwater terrain, collect data.
  	
    •	Environment: Arabian Sea.
  	
    •	Actuators: Propellers, robotic arms.
  	
    •	Sensors: Sonar, cameras.
  	
4.	Shopping for used AI books on the Internet:
   
    •	Performance: Obtain desired AI books within budget.
  	
    •	Environment: Online book marketplaces.
  	
    •	Actuators: Clicks, typing.
  	
    •	Sensors: Search results, prices.
  	
6.	Playing a tennis match:
   
    •	Performance: Win points, match.
  	
    •	Environment: Tennis court with a net, opponent.
  	
    •	Actuators: Muscles, racket.
  	
    •	Sensors: Eyes.
  	
8.	Practicing tennis against a wall:
    
    •	Performance: Improve hitting accuracy and power.
  	
    •	Environment: Tennis court with a wall.
  	
    •	Actuators: Muscles, racket.
  	
    •	Sensors: Eyes.
  	
10.	Performing a high jump:
    
    •	Performance: Clear the bar at the highest possible height.
   	
    •	Environment: High jump track with a bar.
   	
    •	Actuators: Muscles for jumping.
   	
    •	Sensors: Eyes for judging bar height.
   	
12.	Knitting a sweater:
    
    •	Performance: Create a complete and well-knit sweater.
   	
    •	Environment: Crafting area with yarn, needles.
   	
    •	Actuators: Hands, knitting needles.
   	
    •	Sensors: Eyes for inspecting knitting progress.
   	
14.	Bidding on an item at an auction:
    
    •	Performance: Successfully win desired items at the best price.
   	
    •	Environment: Auction platform with items up for bid.
   	
    •	Actuators: Bidding actions.
   	
    •	Sensors: Current bid prices, time remaining.


## Q5
Q5) Assertions:

- True: An agent that senses only partial information about the state cannot be perfectly rational. Perfect rationality implies making decisions based on complete and accurate information. If an agent has only partial information, its decisions may not be optimal. For example, consider a chess-playing agent that can only see a subset of the opponent's pieces. It cannot make perfectly rational moves without knowing the entire state of the board.

- True: There exist task environments in which no pure reflex agent can behave rationally. Pure reflex agents make decisions based solely on the current percept, without considering the history of the percept sequence. In dynamic or partially observable environments, these agents may not exhibit rational behavior. For instance, in a poker game where opponents' moves are not fully observable, a pure reflex agent may not make rational decisions without considering the context.

- False: There does not exist a task environment in which every agent is rational. Rationality depends on making optimal decisions given the available information, and not all agents may possess the capability to do so in every possible scenario.

- False: The input to an agent program is not necessarily the same as the input to the agent function. The agent program may include additional information or preprocessing steps not present in the raw input to the agent function.

- True: Every agent function is implementable by some program/machine combination. An agent function can be translated into a program that processes inputs and produces outputs based on the specified actions of the agent function. This program can be executed on a machine.

- True: Suppose an agent selects its action uniformly at random from the set of possible actions. There exists a deterministic task environment in which this agent is rational. For example, if the environment is such that all actions have an equal chance of leading to a favorable outcome, then a random selection can be considered rational in that specific context.

- True: It is possible for a given agent to be perfectly rational in two distinct task environments. If the agent's decision-making process is designed to optimize its actions based on the specific characteristics of each environment, it can be perfectly rational in both, even if the optimal actions differ.

