# Evo Royal TA

## Why?
The official Royal TA mode has some issues like not reporting times properly to XMLRPC and dynamic time limit not working. This modified version attempts to fix several of these issues.

## Features
- Two new callbacks:
  - `Royal.PlayerFinish` - Triggers when a player finishes the whole map (the last segment of the map) and returns the time it took from first start to the finish of the last segment.
  - `Royal.PlayerFinishSegment` - Triggers every time a player finishes a segment. It also reports which segment and the time it took from first start to the current segment finish.
- Fix for changing the time limit live.

## Callbacks
### Royal.PlayerFinish
* Name: Royal.PlayerFinish
* Type: CallbackArray
* Description: Callback sent when a player finishes all segments.
* Data:
	- Version >=2.0.0:
	```
	[
		{
			"login": "player-login", // The login id of the player
			"racetime" 12345 // the time the player took from first segment to last.
		}
	]
	```

### Royal.PlayerFinishSegment
* Name: Royal.PlayerFinishSegment
* Type: CallbackArray
* Description: Callback sent when a player finishes all segments.
* Data:
	- Version >=2.0.0:
	```
	[
		{
			"login": "player-login", // The login id of the player
			"racetime" 12345 // the time the player took to the current segment
			"segment": <n> // The current segment the player finished
		}
	]
	```