---
BanEnum: Ban status of a Player
ProfileService: Read the official module docs
Kick Messages: Explanation of why these kicks occur.
---

# BanEnum
Here is the full list of ban stats which are used internally in the game.
* **NotBanned = 0:** Default Ban Status
* **PermBanned = 1:** Permanent Ban Enum
* **TempBanned = 2:** Temporary Ban Enum (Ban will be revoked after n amount of time passes)

> [!WARNING]
> Temporary Bans that have expired will not update as NotBanned in the datastore, the Player must join the game for the database to update its data with the NotBanned enum.

# Kick Message Explanations
 ### [LocalKick]: DataStore released Player data.
 * Listener functions subscribed to Profile:ListenToRelease() will be called when the profile is released remotely (Being "ForceLoad"'ed on a remote server) or locally (Profile:Release()). In common practice, the profile will rarely be released before the player leaves the game so it's recommended to simply :Kick() the Player when this happens.

 ### [LocalKick]: Failed to fetch Data from servers, please rejoin.

  This kick message occurs on multiple occasions:
  * When Roblox DataStore servers spit out an Internal Server Error, simply rejoining will fix the issue.
  * If there was a corruption by a nasty bug then the development team should [investigate the issue](#investigating-a-corrupted-profile).
 
# Investigating A Corrupted Profile
 1) Check the profile's data via the Roblox Studio Dev Console `game:GetService("DataStoreService"):GetDataStore("PlayerData"):GetAsync(PLAYER_USERID)`
 2) Make sure the "PlayerDataTemplate" profile template table isn't messed up.
 3) If the profile is still still kinda intact find a better version of the profile via ProfileStore:ProfileVersionQuery() and rollback.
 4) Try reverting the "PlayerDataHandler" script to its old state via the Script History to check if you are the issue. >:(
 5) Pray to god you find a fix before we get another damn dislike on this game.

# [ProfileService Docs](https://madstudioroblox.github.io/ProfileService/api/)
