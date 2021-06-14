# Evo Royal TA

## Why?
The official Royal TA mode has some issues like not reporting times properly to XMLRPC and dynamic time limit not working. This modified version attempts to fix several of these issues.

## Features
- Two new callbacks:
  - `Royal.PlayerFinish` - Triggers when a player finishes the whole map (the last segment of the map) and returns the time it took from first start to the finish of the last segment.
  - `Royal.PlayerFinishSegment` - Triggers every time a player finishes a segment. It also reports which segment and the time it took from first start to the current segment finish.
- Fix for changing the time limit live.
- Ability to set script environment in the settings.

## Install
1. In your server files, copy the `Evo_Royal_TA.Script.txt` file into `UserData/Scripts`.
2. Create a new matchsettings with the custom mode:
```xml
<?xml version="1.0" encoding="utf-8" ?>
<playlist>
        <gameinfos>
                <game_mode>0</game_mode>
                <script_name>Evo_Royal_TA</script_name>
        </gameinfos>
        <mode_script_settings>
                <setting name="S_TimeLimit" type="integer" value="150" />
                <setting name="S_ScriptEnvironment" type="string" value="production" />
        </mode_script_settings>
        
        <startindex>0</startindex>
        <map><file>MyAwesomeRoyalMap.Map.Gbx</file></map>
</playlist>
```

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