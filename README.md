
## Game/Session
- ID
- Start Date/Time Stamp
- End Date/Time Stamp
- have (2-4) Players
- have (106) Tiles
- have Racks = # of players
- have (1) Pool
- have (1) Board
- 3 States (choose 1)
	- New
	- In Progress
	- Completed
- if State == Completed, have (1) Winner

## Tile
- ID
- have (1) color Black, Red, Blue, Orange
- have (1) number 1-13 or Joker
- State?
	- in Player 1 rack
	- in Player 2 rack
	- on Board
	- in Pool
## Rack
- ID
- have tiles 14 tiles at start of game
- count of tiles may increase or decrease as game progresses
- how many tiles are on rack

## Bone Pile/Pool/Bag
- essentially a Rack of all unused tiles
- finite amount of tiles
- fixed values for times
- 106 Tiles total
	- 2 sets of each 1-13 of the four colors
	- 2 Jokers (Color doesn't matter)
	- Single Character Card Value + Color 
		- 0 = 10, J=11, Q=12, K=13
		- B=Black, O= Orange, R=Red, U=Blue
		- XX or ZZ=Joker

## Player/Hand
- ID
- have (1) rack
- Take turns/actions
- have state
- Did you win or lose?

## States
- 1-Taking turn
	- performing action
- 0-Waiting to take Turn
	- can manipulate tiles on rack

## State Changes
- Did the board get updated?
- How many tiles are on your rack?
- Did you win?
- Did the other player win?
- Did all Validation checks pass?
	- if not, draw 3 tiles from the Pool?
- Did you run out of time?
	- if so, draw a tile from the Pool

## Action(s)-Array Choose  Draw vs Place (or Pass if no Tiles in Pool)
- ID
- Draw (1) tile from Bone Pile
	- remove from Pool, 
	- if no tiles available in Pool, then Pass. 
- Place(s) 
	- New Sequence or Set on Board
	- Adjust Sequence or Set on Board
	- Add single tile to Existing Sequence or Set on Board
- Need to validate after Play(s)
- Can do multiple plays
- Time Limit (2 minutes) adjustable?
- First play must be 30 points in one or more groupings

## Winning
- Player with 0 tiles left in Rack

## Board
- have collections of tiles in VALID Run/Sequences or Set/Groups 
- huge blank canvas/grid can place tiles where ever (see Jamison's map maker)
- need to retain previous state before player's turn to undo array
	- store prior state's JSON from REST call 
- Run validation Checks on all tile collections


## Validation Checks
- Run/Sequence:
	- 1 is always played as the lowest number
	- 13 is always played as the highest number
	- All tiles in collection are of same color*
	- Min of  3 tiles 
	- Max of 13 tiles
	- tile's value are sequential/consecutive numerically 
- Set/Group
	- Color must be unique within collection
	- Max of 4 tiles (1 of each color*)
	- Min of 3 tiles
	- Tiles within collection must be same value*
- Jokers
	- Tile replacing the joker must come from rack, not board
	- Tile replacing must result in valid Run/Sequence or Set/Group
	- Joker that has been replaced must be used in same turn with 2 or more tiles from rack.
	- In a Set/Group of 3 tiles can be replaced by 2 different tiles of the missing colors


## Issues/Undefined/Ideas
- Who goes first? RNG?
- hosting application/web to make interactive for 2 players online
	- REST Calls back and forth
	- polling for turns
	- authentication?
	- game id?
	- payload includes 
		- board
		- pool
		- player rack size
		- opponent rack size
- graphics/interactive
	- buttons?
	- Strings for now? 
- Help button with rules?
- House Rules
	- Scoring/Points
	- Number of tiles per draw?
	- time limits (enable vs disable)


## Resources
- Rules: https://imgv2-1-f.scribdassets.com/img/document/335635268/original/486e258924/1596396259?v=1
- http://technicalrex.com/2014/09/02/designing-a-rest-api-for-a-turn-based-game
- https://stackoverflow.com/questions/405588/what-restful-api-would-you-use-for-a-turn-based-game-server
- https://raml.org/
- http://apiworkbench.com/
- http://www.blippee.com/game-instructions/instructions-pressman-rummikub.pdf
- 
