---
BanEnum: Ban status of a Player
ProfileService: Read the official module docs
---

# BanEnum
Here is the full list of ban stats which are used internally in the game.
* **NotBanned = 0:** Default Ban Status
* **PermBanned = 1:** Permanent Ban Enum
* **TempBanned = 2:** Temporary Ban Enum (Ban will be revoked after n amount of time passes)

  **WARNING:** Temporary Bans that have expired will not update as NotBanned in the datastore, the Player must join the game for the database to update its data with NotBanned enum.

# [ProfileService Docs](https://madstudioroblox.github.io/ProfileService/api/)
