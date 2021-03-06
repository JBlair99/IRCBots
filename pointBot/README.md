# pointBot
This is a simple IRC bot that uses the twisted IRC client. It keeps track of points given to users, which are given
through traditional +1, -1, etc. Each user gets 10 "gift points" to pass out every calendar day.

## Admin Commands:
- `pointBot, start` (starts the point game [i.e. allows point exchanges])
- `pointBot, stop` (ends game [i.e. disallows point exchanges])
- `pointBot, auto` (automatically starts and stops the point game based on the time of day [see privmsg()])
- `pointBot, reset` (refreshes user gift point totals)
- `pointBot, save` (saves list of winners || also gets saved at the end of every day)
- `pointBot, restore` (restores winners from save file || also restores automatically on run)
- `pointBot, say <msg>` (sends message to channel as the bot)
- `pointBot, msg <nick> <msg>` (sends PM to user as the bot)
- `pointBot, me <action>` (performs a /me command as the bot)
- `pointBot, status <user>` (returns status of player via PM; also triggered by user PMs)
- `pointBot, setpts <nick/all> <points>` (set points for user)
- `pointBot, setgp <nick/all> <points>` (set points for user)
- `pointBot, ignore <nick>` (adds user to the ignore list; removes from game)
- `pointBot, unignore <nick>` (removes a user from the ignore list; adds back to game)
		 
 ## User Commands
- `pointBot, help` (command list)
- `pointBot, rules` (bot introduction)
- `pointBot, points` (list of active players and points)
- `+/-<pts> [to] <nick> [reason]` (point exchange)
- A PM to pointBot will show you your current status (gift points and total points)
		 
## Usage Notes
#### Setup
- Check the IRC info in the class definition and make sure it is correct.
- Check main() and verify the IRC server is correct.
- Make sure the file paths are correct.
- Choose the start/stop hours.
- Then run pointBot.py from command line to join your chosen channel.
		   
#### Starting the point game:
- If you're starting the game for the first time that day, run the "reset" command. 
- If you're resuming a game midway after a reboot, run the "start" command. 
- Only run the "auto" command while the point game is already running, or during off hours -- it triggers off of messages sent, so if pointBot isn't set up yet it'll disrupt things. After that, though, it's set and forget.
	
#### Restore files:
- The points file stores users as last_nick:ip:gift_points:total_points. Only edit manually if an issue occurs.
- The ignore file stores only IPs. Only edit manually if an issue occurs.
- The bot file stores nicks (since bot names should not change often). This should be edited manually.

NOTE: I've run into a couple issues with multiple nicks on the same IP (account stuck logged in) and even IPs changing due to modem testing, but this is uncommon enough that it can be dealt with by adding nicks to the bot list, ignoring users ("ignore"), or deleting point entries manually.