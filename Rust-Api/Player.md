
#Can Afford Upgrade

1. Called when the resources for an upgrade are checked  
2. Returning true or false overrides default behavior

```c
bool CanAffordUpgrade(BasePlayer player, BuildingBlock block, BuildingGrade.Enum grade)
{
    Puts("CanAffordUpgrade works!");
    return true;
}
```
#Can Assign Bed

1. Called when a player attempts to assign a bed or sleeping bag to another player  
2. Returning a non-null value overrides default behavior

```c
object CanAssignBed(BasePlayer player, SleepingBag bag, ulong targetPlayerId)
{
    Puts("CanAssignBed works!");
    return null;
}
```
#Can Update Sign

1. Called when the player attempts to change the text on a sign or lock it, or update a photo frame  
2. Returning true or false overrides default behavior

```c
bool CanUpdateSign(BasePlayer player, Signage sign)
{
    Puts("CanUpdateSign works!");
    return true;
}
bool CanUpdateSign(BasePlayer player, PhotoFrame photoFrame)
{
    Puts("CanUpdateSign works!");
    return true;
}
```

#On User Chat

1. Called when a player sends a chat message to the server  
2. Returning true overrides default behavior of chat, not commands

```c
object OnUserChat(IPlayer player, string message)
{
    Puts($"{player.Name} said: {message}");
    return null;
}
```
#On Player Command

1. Useful for intercepting players' commands before their handling  
2. Returning a non-null value overrides default behavior

```c
object OnPlayerCommand(BasePlayer player, string command, string[] args)
{
    Puts("OnPlayerCommand works!");
    return null;
}
```
#On User Command

1. Useful for intercepting players' commands before their handling  
2. Returning a non-null value overrides default behavior

```c
object OnUserCommand(IPlayer player, string command, string[] args)
{
    Puts("OnUserCommand works!");
    return null;
}
```

#On Player Revive

1. Called before the recover after reviving with a medical tool  
2. Useful for canceling the reviving  
3. Returning a non-null value cancels default behavior

```c
object OnPlayerRevive(BasePlayer reviver, BasePlayer player)
{
    Puts($"{reviver.displayName} revived {player.displayName}");
    return null;
}
```

#Can Lock

1. Useful for canceling the lock action
2. Returning a non-null value cancels default behavior  
3. object CanLock(BasePlayer player, BaseLock baseLock)

```c
{
    Puts("CanLock works!");
    return null;
}
```
#On Melee Attack

1. Useful for canceling melee attacks  
2. Returning a non-null value cancels default behavior

```c
object OnMeleeAttack(BasePlayer player, HitInfo info)
{
    Puts("OnMeleeAttack works!");
    return null;
}
```
#On Player Recovered

1. Called when the player was recovered  
2. No return behavior

```c
void OnPlayerRecovered(BasePlayer player)
{
    Puts("OnPlayerRecovered works!");
}
```

#Can Push Boat

1. Useful for canceling boat push  
2. Returning a non-null value cancels default behavior

```c
object CanPushBoat(BasePlayer player, MotorRowboat boat)
{
    Puts("CanPushBoat works!");
    return null;
}
```

#Can Deploy Item

1. Useful for denying items' deployment  
2. Returning a non-null value cancels default behavior

```c
object CanDeployItem(BasePlayer player, Deployer deployer, NetworkableId entityId)
{
    Puts("CanDeployItem works!");
    return null;
}
```
#On Player Assist

1. Called when a player tries to assist target player (when target is wounded)  
2. Returning a non-null value cancels default behavior

```c
object OnPlayerAssist(BasePlayer target, BasePlayer player)
{
    Puts("OnPlayerAssist works!");
    return null;
}
```

#On Player Set Info
1. Called when setting player's information (aka console variables)  
2. No return behavior

```c
void OnPlayerSetInfo(Connection connection, string key, string value)
{
    Puts($"{connection.userid}: {key} was set to {value}");
}
```

#Can Spectate Target

1. Called when spectate target is attempting to update  
2. Returning a non-null value cancels default behavior

```c
object CanSpectateTarget(BasePlayer player, string filter)
{
    Puts($"{player.displayName} tries to spectate with a filter: {filter}");
    return null;
}
```

#On Active Item Change

1. Called when active item is attempting to update  
2. Returning a non-null value cancels default behavior

```c
object OnActiveItemChange(BasePlayer player, Item oldItem, ItemId newItemId)
{
    Puts("OnActiveItemChange works!");
    return null;
}
```

#On Active Item Changed

1. Called when active item was changed  
2. No return behavior

```c
void OnActiveItemChanged(BasePlayer player, Item oldItem, Item newItem)
{
    Puts("OnActiveItemChanged works!");
}
```
#On Pay For Upgrade

1. Called when player is paying for an upgrade. Useful for preventing paying for block upgrade  
2. Returning a non-null value cancels default behavior

```c
object OnPayForUpgrade(BasePlayer player, BuildingBlock block, ConstructionGrade gradeTarget)
{
    Puts("OnPayForUpgrade works!");
    return null;
}
```

#On Map Marker Remove

1. Called when trying to remove a marker  
2. Returning a non-null value cancels default behaviour

```c
object OnMapMarkerRemove(BasePlayer player, MapNote note)
{
    Puts("OnMapMarkerRemove works!");
    return null;
}
```

#On Map Marker Add

1. Called when trying to add a marker  
2. Returning a non-null value cancels default behavior

```c
object OnMapMarkerAdd(BasePlayer player, MapNote note)
{
    Puts("OnMapMarkerAdd works!");
    return null;
}
```

#On Map Marker Added

1. Called after a marker was added  
2. No return behavior

```c
void OnMapMarkerAdded(BasePlayer player, MapNote note)
{
    Puts("OnMapMarkerAdded works!");
}
```

#On Map Markers Clear

1. Called when trying to clear map markers  
2. Returning a non-null value cancels default behavior

```c
object OnMapMarkersClear(BasePlayer player, List<MapNote> notes)
{
    Puts("OnMapMarkersClear works!");
    return null;
}
```
#On Map Markers Cleared

1. Called after markers were cleared  
2. No return behavior

```c
void OnMapMarkersCleared(BasePlayer player, List<MapNote> notes)
{
    Puts("OnMapMarkersCleared works!");
}
```

#On Pay For Placement
1. Called when a player is paying for placement. Useful for preventing paying for placing deployables, building blocks and etc  
2. Returning a non-null value cancels default behavior

```c
object OnPayForPlacement(BasePlayer player, Planner planner, Construction construction)
{
    Puts("OnPayForPlacement works!");
    return null;
}
```

#Can Afford To Place
1. Useful for ignoring resource requirements for placement  
2. Returning true or false overrides default behavior
 
```c
bool CanAffordToPlace(BasePlayer player, Planner planner, Construction construction)
{
    Puts("CanAffordToPlace works!");
    return false;
}
```

#On Player Keep Alive

1. Called before a player is kept alive (Example: You started "helping" player, it keeps him alive for at least 10 seconds more to be sure he won't die until you finish picking him up)  
2. Returning a non-null value cancels default behavior

```c
object OnPlayerKeepAlive(BasePlayer player, BasePlayer target)
{
    Puts("OnPlayerKeepAlive works!");
    return null;
}
```

#On Send Command

1. Called before a command is sent from the server to a player (or a group of players)  
2. Usually commands aren't sent to a group of players, so in most cases it's safe to use only OnSendCommand with a single Connection.  
3. Returning a non-null value overwrites command arguments

```c
object OnSendCommand(List<Connection> connections, string command, object[] args)
{
    Puts("OnSendCommand works!");
    return null;
}

object OnSendCommand(Connection connection, string command, object[] args)
{
    Puts("OnSendCommand works!");
    return null;
}
```
#On Broadcast Command

1. Called before a command is broadcasted to all connected clients  
2. Returning a non-null value overwrites command arguments

```c
object OnBroadcastCommand(string command, object[] args)
{
    Puts("OnBroadcastCommand works!");
    return null;
}
```

#On User Respawn

1. Called when a player is respawning  
2. No return behavior

```c
void OnUserRespawn(IPlayer player)
{
    Puts("OnUserRespawn works!");
}
```

#On User Respawned

1. Called after a player has respawned  
2. No return behavior

```c
void OnUserRespawned(IPlayer player)
{
    Puts("OnUserRespawned works!");
}
```

#On Player Reported

1. Called when a player has reported someone via F7  
2. No return behavior

```c
void OnPlayerReported(BasePlayer reporter, string targetName, string targetId, string subject, string message, string type)
{
    Puts($"{reporter.displayName} reported {targetName} for {subject}.");
}
```

#On Player Corpse

1. Called when a non-null corpse has just been spawned  
2. No return behavior

```c
void OnPlayerCorpse(BasePlayer player, BaseCorpse corpse)
{
    Puts($"A corpse for {player.displayName} has just been spawned!");
}
```

#Can Use Wires

1. Useful for allowing or preventing a player from using wires  
2. Returning a non-null value overrides default behavior

```c
object CanUseWires(BasePlayer player)
{
    Puts($"{player.displayName} has just tried to use wires");
    return null;
}
```

#On Player Corpse Spawn

1. Called when a non-null corpse is about to spawn  
2. Returning a non-null value overrides default behavior

```c
object OnPlayerCorpseSpawn(BasePlayer player)
{
    Puts("OnPlayerCorpseSpawn works!");
    return null;
}
```

#On Player Corpse Spawned

1. Called when a non-null corpse has just been spawned
2. No return behavior

```c
void OnPlayerCorpseSpawned(BasePlayer player, PlayerCorpse corpse)
{
    Puts("OnPlayerCorpseSpawned works!");
}
```

#On User Connected

1. Called after a player has been approved and has connected to the server  
2. No return behavior

```c
void OnUserConnected(IPlayer player)
{
    Puts($"{player.Name} ({player.Id}) connected from {player.Address}");

    if (player.IsAdmin)
    {
        Puts($"{player.Name} ({player.Id}) is admin");
    }

    Puts($"{player.Name} is {(player.IsBanned ? "banned" : "not banned")}");

    server.Broadcast($"Welcome {player.Name} to {server.Name}!");
}
```

#On User Disconnected

1. Called after a player has disconnected from the server  
2. No return behavior

```c
void OnUserDisconnected(IPlayer player)
{
    Puts($"{player.Name} ({player.Id}) disconnected");
}
```

#Can Be Targeted

1. Called when an autoturret, flame turret, shotgun trap, or helicopter turret is attempting to target the player  
2. Returning true or false overrides default behavior

```c
bool CanBeTargeted(BaseCombatEntity player, MonoBehaviour behaviour)
{
    Puts("CanBeTargeted works!");
    return true;
}
```

#Can Be Wounded

1. Called when any damage is attempted on player  
2. Returning true or false overrides default behavior

```c
bool CanBeWounded(BasePlayer player, HitInfo info)
{
    Puts("CanBeWounded works!");
    return true;
}
```

#Can Build

1. Called when the player tries to build something  
2. Returning a non-null value overrides default behavior

```c
object CanBuild(Planner planner, Construction prefab, Construction.Target target)
{
    Puts("CanBuild works!");
    return null;
}
```

CanBypassQueue
Called before the player is added to the connection queue
Returning true will bypass the queue, returning nothing will by default queue the player
bool CanBypassQueue(Network.Connection connection)
{
    Puts("CanBypassQueue works!");
    return true;
}
CanChangeCode
Called when a player tries to change the code on a codelock
Returning a non-null value overrides default behavior
object CanChangeCode(BasePlayer player, CodeLock codeLock, string newCode, bool isGuestCode)
{
    Puts("CanChangeCode works!");
    return null;
}
CanChangeGrade
Called when a player tries to change a building grade
Returning true or false overrides default behavior
bool CanChangeGrade(BasePlayer player, BuildingBlock block, BuildingGrade.Enum grade)
{
    Puts("CanChangeGrade works!");
    return true;
}
CanCraft
Called when the player attempts to craft an item
Returning true or false overrides default behavior
bool CanCraft(ItemCrafter itemCrafter, ItemBlueprint bp, int amount)
{
    Puts("CanCraft works!");
    return true;
}
bool CanCraft(PlayerBlueprints playerBlueprints, ItemDefinition itemDefinition, int skinItemId)
{
    Puts("CanCraft works!");
    return true;
}
CanClientLogin
Called when the player is attempting to login
Returning a string will use the string as the error message
Returning true allows the connection, returning nothing will by default allow the connection, returning anything else will reject it with an error message
object CanClientLogin(Network.Connection connection)
{
    Puts("CanClientLogin works!");
    return true;
}
CanUserLogin
Called when a player is attempting to connect to the server
Returning a string will kick the user with this reason. Returning a non-null value overrides default behavior
object CanUserLogin(string name, string id, string ipAddress)
{
    if (name.ToLower().Contains("admin"))
    {
        Puts($"{name} ({id}) at {ipAddress} tried to connect with 'admin' in name");
        return "Sorry, your name cannot have 'admin' in it";
    }

    return true;
}
OnUserApproved
Called after a player is approved to connect to the server
No return behavior
void OnUserApproved(string name, string id, string ipAddress)
{
    Puts($"{name} ({id}) at {ipAddress} has been approved to connect");
}
CanDemolish
Called when a player tries to demolish a building block
Returning true or false overrides default behavior
bool CanDemolish(BasePlayer player, BuildingBlock block, BuildingGrade.Enum grade)
{
    Puts("CanDemolish works!");
    return true;
}
CanHackCrate
Called when a player starts hacking a locked crate
Returning a non-null value overrides default behavior
object CanHackCrate(BasePlayer player, HackableLockedCrate crate)
{
    Puts("CanHackCrate works!");
    return null;
}
OnUserNameUpdated
Called when a player's stored nickname has been changed
No return behavior
void OnUserNameUpdated(string id, string oldName, string newName)
{
    Puts($"Player name changed from {oldName} to {newName} for ID {id}");
}
CanDismountEntity
Called when the player attempts to dismount an entity
Returning a non-null value overrides default behavior
object CanDismountEntity(BasePlayer player, BaseMountable entity)
{
    Puts("CanDismountEntity works!");
    return null;
}
OnUserGroupAdded
Called when a player has been added to a group
No return behavior
void OnUserGroupAdded(string id, string groupName)
{
    Puts($"Player '{id}' added to group: {groupName}");
}
OnUserGroupRemoved
Called when a player has been removed from a group
No return behavior
void OnUserGroupRemoved(string id, string groupName)
{
    Puts($"Player '{id}' removed from group: {groupName}");
}
CanEquipItem
Called when the player attempts to equip an item
Returning true or false overrides default behavior
bool CanEquipItem(PlayerInventory inventory, Item item, int targetPos)
{
    Puts("CanEquipItem works!");
    return true;
}
OnExperimentStart
Called when the player attempts to experiment with at a workbench
Returning a non-null value overrides default behavior
object OnExperimentStart(Workbench workbench, BasePlayer player)
{
    Puts("OnExperimentStart works!");
    return null;
}
OnUserPermissionGranted
Called when a permission has been granted to a player
No return behavior
void OnUserPermissionGranted(string id, string permName)
{
    Puts($"Player '{id}' granted permission: {permName}");
}
OnUserPermissionRevoked
Called when a permission has been revoked from a player
No return behavior
void OnUserPermissionRevoked(string id, string permName)
{
    Puts($"Player '{id}' revoked permission: {permName}");
}
OnExperimentStarted
Called after the experimentation has started
No return behaviour
void OnExperimentStarted(Workbench workbench, BasePlayer player)
{
    Puts("OnExperimentStarted works!");
}
OnUserKicked
Called when a player has been kicked from the server
No return behavior
void OnUserKicked(IPlayer player, string reason)
{
    Puts($"Player {player.Name} ({player.Id}) was kicked");
}
OnExperimentEnd
Called when an experiment is about to end
Returning a non-null value overrides defualt behaviour.
object OnExperimentEnd(Workbench workbench)
{
    Puts("OnExperimentEnd works!");
    return null;
}
OnExperimentEnded
Called after the experiment has finished
No return behaviour
void OnExperimentEnded(Workbench workbench)
{
    Puts("OnExperimentEnded works!");
}
OnUserBanned
Called when a player has been banned from the server
Will have reason available if provided
No return behavior
void OnUserBanned(string name, string id, string ipAddress, string reason)
{
    Puts($"Player {name} ({id}) at {ipAddress} was banned: {reason}");
}
CanHideStash
Called when a player tries to hide a stash
Returning a non-null value overrides default behavior
object CanHideStash(BasePlayer player, StashContainer stash)
{
    Puts("CanHideStash works!");
    return null;
}
OnUserUnbanned
Called when a player has been unbanned from the server
No return behavior
void OnUserUnbanned(string name, string id, string ipAddress)
{
    Puts($"Player {name} ({id}) at {ipAddress} was unbanned");
}
CanLootPlayer
Called when the player attempts to loot another player
Returning true or false overrides default behavior
bool CanLootPlayer(BasePlayer target, BasePlayer looter)
{
    Puts("CanLootPlayer works!");
    return true;
}
CanLootEntity
Called when the player starts looting a DroppedItemContainer, LootableCorpse, ResourceContainer, BaseRidableAnimal, or StorageContainer entity
Returning a non-null value overrides default behavior
object CanLootEntity(BasePlayer player, DroppedItemContainer container)
{
    Puts("CanLootEntity works!");
    return null;
}
object CanLootEntity(BasePlayer player, LootableCorpse  corpse)
{
    Puts("CanLootEntity works!");
    return null;
}
object CanLootEntity(BasePlayer player, ResourceContainer container)
{
    Puts("CanLootEntity works!");
    return null;
}
object CanLootEntity(BasePlayer player, BaseRidableAnimal animal)
{
    Puts("CanLootEntity works!");
    return null;
}
object CanLootEntity(BasePlayer player, StorageContainer container)
{
    Puts("CanLootEntity works!");
    return null;
}
CanMountEntity
Called when the player attempts to mount an entity
Returning a non-null value overrides default behavior
object CanMountEntity(BasePlayer player, BaseMountable entity)
{
    Puts("CanMountEntity works!");
    return null;
}
CanPickupEntity
Called when a player attempts to pickup a deployed entity (AutoTurret, BaseMountable, BearTrap, DecorDeployable, Door, DoorCloser, ReactiveTarget, SamSite, SleepingBag, SpinnerWheel, StorageContainer, etc.)
Returning true or false overrides default behavior
bool CanPickupEntity(BasePlayer player, BaseEntity entity)
{
    Puts("CanPickupEntity works!");
    return true;
}
CanPickupLock
Called when a player attempts to pickup a lock
Returning true or false overrides default behavior
bool CanPickupLock(BasePlayer player, BaseLock baseLock)
{
    Puts("CanPickupLock works!");
    return true;
}
CanRenameBed
Called when the player attempts to rename a bed or sleeping bag
Returning a non-null value overrides default behavior
object CanRenameBed(BasePlayer player, SleepingBag bed, string bedName)
{
    Puts("CanRenameBed works!");
    return null;
}
CanResearchItem
Called when the player attempts to research an item
Returning a non-null value overrides default behavior
object CanResearchItem(BasePlayer player, Item targetItem)
{
    Puts("CanResearchItem works!");
    return null;
}
CanUseLockedEntity
Called when the player tries to use an entity that is locked
Returning true or false overrides default behavior
bool CanUseLockedEntity(BasePlayer player, BaseLock baseLock)
{
    Puts("CanUseLockedEntity works!");
    return true;
}
CanSeeStash
Called when a player is looking at a hidden stash
Returning a non-null value overrides default behavior
object CanSeeStash(BasePlayer player, StashContainer stash)
{
    Puts("CanSeeStash works!");
    return null;
}
OnStashExposed
Called when a player reveals a hidden stash
No return behavior
void OnStashExposed(StashContainer stash, BasePlayer player)
{
    Puts("OnStashExposed works");
}
OnStashHidden
Called when a player hides a stash
No return behavior
void OnStashHidden(StashContainer stash, BasePlayer player)
{
    Puts("OnStashHidden works!");
}
CanSetBedPublic
Called when a player tries to set a bed public
Returning a non-null value overrides default behavior
object CanSetBedPublic(BasePlayer player, SleepingBag bed)
{
    Puts("CanSetBedPublic works!");
    return null;
}
CanUnlock
Called when the player tries to unlock a keylock or codelock
Returning a non-null value overrides default behavior
object CanUnlock(BasePlayer player, BaseLock baseLock)
{
    Puts("CanUnlock works!");
    return null;
}
CanUseMailbox
Called when the player tries to use a mailbox
Returning true or false overrides default behavior
bool CanUseMailbox(BasePlayer player, Mailbox mailbox)
{
    Puts("CanUseMailbox works!");
    return true;
}
CanUseUI
Called when the player attempts to use a custom UI
Returning a non-null value overrides default behavior
object CanUseUI(BasePlayer player, string json)
{
    Puts("CanUseUI works!");
    return null;
}
CanWearItem
Called when the player attempts to equip an item
Returning a non-null value overrides default behavior
object CanWearItem(PlayerInventory inventory, Item item, int targetSlot)
{
    Puts("CanWearItem works!");
    return null;
}
OnClientAuth
Called when the player is giving server connection authorization information
No return behavior
void OnClientAuth(Connection connection)
{
    Puts("OnClientAuth works!");
}
OnDestroyUI
Called when a custom UI is destroyed for the player
No return behavior
void OnDestroyUI(BasePlayer player, string json)
{
    Puts("OnDestroyUI works!");
}
OnFindSpawnPoint
Useful for controlling player spawnpoints (like making all spawns occur in a set area)
Return a BasePlayer.SpawnPoint object to use that spawnpoint
void OnFindSpawnPoint(BasePlayer player)
{
    Puts("OnFindSpawnPoint works!");
}
OnLootEntity
Called when the player starts looting an entity
No return behavior
void OnLootEntity(BasePlayer player, BaseEntity entity)
{
    Puts("OnLootEntity works!");
}
OnLootEntityEnd
Called when the player stops looting an entity
No return behavior
void OnLootEntityEnd(BasePlayer player, BaseCombatEntity entity)
{
    Puts("OnLootEntityEnd works!");
}
OnLootItem
Called when the player starts looting an item
No return behavior
void OnLootItem(PlayerLoot playerLoot, Item item)
{
    Puts("OnLootItem works!");
}
OnLootPlayer
Called when the player starts looting another player
No return behavior
void OnLootPlayer(BasePlayer player, BasePlayer target)
{
    Puts("OnLootPlayer works!");
}
OnPlayerAttack
Useful for modifying an attack before it goes out
hitInfo.HitEntity should be the entity that this attack would hit
Returning a non-null value overrides default behavior
object OnPlayerAttack(BasePlayer attacker, HitInfo info)
{
    Puts("OnPlayerAttack works!");
    return null;
}
OnPlayerBanned
Called when the player is banned (Facepunch, EAC, server ban, etc.)
No return behavior
void OnPlayerBanned(string name, ulong id, string address, string reason)
{
    Puts("OnPlayerBanned works!");
}
OnPlayerChat
Called when the player sends chat to the server
Returning a non-null value overrides default behavior of chat, not commands
object OnPlayerChat(BasePlayer player, string message, Chat.ChatChannel channel)
{
    Puts("OnPlayerChat works!");
    return null;
}
OnPlayerConnected
Called after the player object is created, but before the player has spawned
No return behavior
void OnPlayerConnected(BasePlayer player)
{
    Puts("OnPlayerConnected works!");
}
OnPlayerDeath
Called when the player is about to die
HitInfo may be null sometimes
Returning a non-null value overrides default behavior
object OnPlayerDeath(BasePlayer player, HitInfo info)
{
    Puts("OnPlayerDeath works!");
    return null;
}
OnPlayerDisconnected
Called after the player has disconnected from the server
No return behavior
void OnPlayerDisconnected(BasePlayer player, string reason)
{
    Puts("OnPlayerDisconnected works!");
}
OnPlayerDropActiveItem
Called when the player drops their active held item
No return behavior
void OnPlayerDropActiveItem(BasePlayer player, Item item)
{
    Puts("OnPlayerDropActiveItem works!");
}
OnPlayerHealthChange
Called just before the player's health changes
Returning a non-null value cancels the health change
object OnPlayerHealthChange(BasePlayer player, float oldValue, float newValue)
{
    Puts("OnPlayerHealthChange works!");
    return null;
}
OnPlayerInput
Called when input is received from a connected client
No return behavior
void OnPlayerInput(BasePlayer player, InputState input)
{
    Puts("OnPlayerInput works!");
}
OnPlayerKicked
Called after the player is kicked from the server
No return behavior
void OnPlayerKicked(BasePlayer player, string reason)
{
    Puts("OnPlayerKicked works!");
}
OnPlayerLand
Called just before the player lands on the ground
Returning a non-null value overrides default behavior
object OnPlayerLand(BasePlayer player, float num)
{
    Puts("OnPlayerLand works!");
    return null;
}
OnPlayerLanded
Called when the player landed on the ground
No return behavior
void OnPlayerLanded(BasePlayer player, float num)
{
    Puts("OnPlayerLanded works!");
}
OnPlayerLootEnd
Called when the player stops looting
No return behavior
void OnPlayerLootEnd(PlayerLoot inventory)
{
    Puts("OnPlayerLootEnd works!");
}
OnPlayerMetabolize
Called after the player's metabolism has been changed
No return behavior
void OnPlayerMetabolize(PlayerMetabolism metabolism, BaseCombatEntity entity, float delta)
{
    Puts("OnPlayerMetabolize works!");
}
OnPlayerRecover
Called when the player is about to recover from the 'wounded' state
Returning a non-null value overrides default behavior
object OnPlayerRecover(BasePlayer player)
{
    Puts("OnPlayerRecover works!");
    return null;
}
OnPlayerRespawn
Called when a player is attempting to respawn
Returning a BasePlayer.SpawnPoint (takes a position and rotation), overrides the respawn location, for the variant that receives a BasePlayer.SpawnPoint argument
Returning a SleepingBag overrides the respawn location, for the variant that receives a SleepingBag argument
object OnPlayerRespawn(BasePlayer player, BasePlayer.SpawnPoint spawnPoint)
{
    Puts("OnPlayerRespawn works!");
    return null;
}
object OnPlayerRespawn(BasePlayer player, SleepingBag sleepingBag)
{
    Puts("OnPlayerRespawn works!");
    return null;
}
OnPlayerRespawned
Called when the player has respawned (specifically when they click the "Respawn" button)
ONLY called after the player has transitioned from dead to not-dead, so not when they're waking up
This means it's possible for the player to connect and disconnect from a server without OnPlayerRespawned ever triggering for them
No return behavior
void OnPlayerRespawned(BasePlayer player)
{
    Puts("OnPlayerRespawned works!");
}
OnRespawnInformationGiven
Called when a player is about to be sent respawn information
No return behavior
void OnRespawnInformationGiven(BasePlayer player, RespawnInformation respawnInformation)
{
    Puts("OnRespawnInformationGiven works!");
}
OnPlayerSleep
Called when the player is about to go to sleep
Returning a non-null value overrides default behavior
object OnPlayerSleep(BasePlayer player)
{
    Puts("OnPlayerSleep works!");
    return null;
}
OnPlayerSleepEnded
Called when the player awakes
No return behavior
void OnPlayerSleepEnded(BasePlayer player)
{
    Puts("OnPlayerSleepEnded works!");
}
OnPlayerSpawn
Called when a player is attempting to spawn for the first time
Returning true overrides default behavior
object OnPlayerSpawn(BasePlayer player)
{
    Puts("OnPlayerSpawn works!");
    return null;
}
OnPlayerSpectate
Called when the player starts spectating
Returning a non-null value overrides default behavior
object OnPlayerSpectate(BasePlayer player, string spectateFilter)
{
    Puts("OnPlayerSpectate works!");
    return null;
}
OnPlayerSpectateEnd
Called when the player stops spectating
Returning a non-null value stops the spectate from ending
object OnPlayerSpectateEnd(BasePlayer player, string spectateFilter)
{
    Puts("OnPlayerSpectateEnd works!");
    return null;
}
OnPlayerTick
Returning a non-null value overrides default behavior
object OnPlayerTick(BasePlayer player, PlayerTick msg, bool wasPlayerStalled)
{
    Puts("OnPlayerTick works!");
    return null;
}
OnPlayerViolation
Called when the player triggers an anti-hack violation
Returning a non-null value overrides default behavior
object OnPlayerViolation(BasePlayer player, AntiHackType type, float amount)
{
    Puts("OnPlayerViolation works!");
    return null;
}
OnPlayerVoice
Called when the player uses the in-game voice chat
Returning a non-null value overrides default behavior
object OnPlayerVoice(BasePlayer player, Byte[] data)
{
    Puts("OnPlayerVoice works!");
    return null;
}
OnPlayerWound
Called when the player is about to go down to the 'wounded' state
source might be null, check it before use
Returning a non-null value cancels the wounded state
object OnPlayerWound(BasePlayer player, HitInfo info)
{
    Puts("OnPlayerWound works!");
    return null;
}
OnRunPlayerMetabolism
Called before a metabolism update occurs for the specified player
Metabolism update consists of managing the player's temperature, health etc.
You can use this to turn off or change certain aspects of the metabolism, either by editing values before returning, or taking complete control of the method
Returning a non-null value cancels the update
object OnRunPlayerMetabolism(PlayerMetabolism metabolism, BasePlayer player, float delta)
{
    Puts("OnRunPlayerMetabolism works!");
    return null;
}
OnUserApprove
Used by RustCore and abstracted into CanClientLogin
Returning a non-null value overrides default behavior, plugin should call Reject if it does this
object OnUserApprove(Network.Connection connection)
{
    Puts("OnUserApprove works!");
    return null;
}
OnDefaultItemsReceive
Called when a player is about to receive default items
Returning a non-null value overrides default behavior
object OnDefaultItemsReceive(PlayerInventory inventory)
{
    Puts("OnDefaultItemsReceive works!");
    return null;
}
OnDefaultItemsReceived
Called after a player has received default items
Returning a non-null value overrides default behavior
void OnDefaultItemsReceived(PlayerInventory inventory)
{
    Puts("OnDefaultItemsReceived works!");
}
OnAnalysisComplete
Called right after a player completes a survey crater analysis
No return behavior
void OnAnalysisComplete(SurveyCrater surveyCrater, BasePlayer player)
{
    Puts("OnAnalysisComplete works!");
}
OnNpcConversationStart
Called when a player tries to start a conversation with an NPC
Returning a non-null value overrides default behavior
object OnNpcConversationStart(NPCTalking npcTalking, BasePlayer player, ConversationData conversationData)
{
    Puts("OnNpcConversationStart works!");
    return null;
}
OnNpcConversationRespond
Called when a player chooses an NPC conversation response
Returning a non-null value overrides default behavior
object OnNpcConversationRespond(NPCTalking npcTalking, BasePlayer player, ConversationData conversationData, ConversationData.ResponseNode responseNode)
{
    Puts("OnNpcConversationRespond works!");
    return null;
}
OnNpcConversationResponded
Called right after a player's chosen NPC conversation response has been processed
No return behavior
void OnNpcConversationResponded(NPCTalking npcTalking, BasePlayer player, ConversationData conversationData, ConversationData.ResponseNode responseNode)
{
    Puts("OnNpcConversationResponded works!");
}
OnNpcConversationEnded
Called right after a player has ended an NPC conversation
No return behavior
void OnNpcConversationEnded(NPCTalking npcTalking, BasePlayer player)
{
    Puts("OnNpcConversationEnded works!");
}
OnNetworkGroupEntered
Called after a player has entered a network group
No return behavior
void OnNetworkGroupEntered(BasePlayer player, Network.Visibility.Group group)
{
    Puts("OnNetworkGroupEntered works!");
}
OnNetworkGroupLeft
Called after a player has left a network group
No return behavior
void OnNetworkGroupLeft(BasePlayer player, Network.Visibility.Group group)
{
    Puts("OnNetworkGroupLeft works!");
}
OnDemoRecordingStart
Called right before a demo of a player starts recording
Returning a non-null value overrides default behavior
object OnDemoRecordingStart(string filename, BasePlayer player)
{
    Puts("OnDemoRecordingStart works!");
    return null;
}
OnDemoRecordingStarted
Called after a demo of a player has started recording
No return behavior
void OnDemoRecordingStarted(string filename, BasePlayer player)
{
    Puts("OnDemoRecordingStarted works!");
}
OnDemoRecordingStop
Called right before a demo of a player stops recording
Returning a non-null value overrides default behavior
object OnDemoRecordingStop(string filename, BasePlayer player)
{
    Puts("OnDemoRecordingStop works!");
    return null;
}
OnDemoRecordingStopped
Called after a demo of a player has stopped recording
No return behavior
void OnDemoRecordingStopped(string filename, BasePlayer player)
{
    Puts("OnDemoRecordingStopped works!");
}
OnLootNetworkUpdate
Called when a player is trying to loot a container or a container they are looting has changed its contents
Returning a non-null value overrides default behavior
object OnLootNetworkUpdate(PlayerLoot loot)
{
    Puts("OnLootNetworkUpdate works!");
    return null;
}
OnInventoryNetworkUpdate
Called after a player's inventory contents have changed, before it is sent over the network to one or more clients
Returning a non-null value overrides default behavior
object OnInventoryNetworkUpdate(PlayerInventory inventory, ItemContainer container, ProtoBuf.UpdateItemContainer updateItemContainer, PlayerInventory.Type type, PlayerInventory.PlayerInventory.NetworkInventoryMode networkInventoryMode)
{
    Puts("OnInventoryNetworkUpdate works!");
    return null;
}
OnPlayerAddModifiers
Called after a player consumes an item such as tea that is about to apply modifiers
Returning a non-null value overrides default behavior (prevents the modifiers from being applied)
object OnPlayerAddModifiers(BasePlayer player, Item item, ItemModConsumable consumable)
{
    Puts("OnPlayerAddModifiers works!");
    return null;
}
OnThreatLevelUpdate
Called when a player's threat level is about to be updated
Returning a non-null value cancels default behavior
object OnThreatLevelUpdate(BasePlayer player)
{
    Puts("OnThreatLevelUpdate works!");
    return null;
}
CanUseGesture
Called when a player attempts to use a gesture
Returning true or false overrides default behavior
bool? CanUseGesture(BasePlayer player, GestureConfig gesture)
{
    Puts("CanUseGesture works!");
    return null;
}
OnCentralizedBanCheck
Called when a player is about to be checked in the centralized ban database
Returning a non-null value cancels default behavior
object OnCentralizedBanCheck(Network.Connection connection)
{
    Puts("OnCentralizedBanCheck works!");
    return null;
}
OnClientCommand
Useful for intercepting players' commands before their handling
Called before OnPlayerCommand and OnUserCommand
Returning a non-null value overrides default behavior
object OnClientCommand(Connection connection, string command)
{
    Puts("OnClientCommand works!");
    return null;
}
OnCorpsePopulate
Called when an NPC player corpse is about to be populated with loot
Returning a BaseCorpse overrides default behavior
BaseCorpse OnCorpsePopulate(BasePlayer npcPlayer, BaseCorpse corpse)
{
    Puts("OnCorpsePopulate works!");
    return null;
}
CanSetRelationship
Called when a player's relationship with another is about to be updated
Returning true or false overrides default behavior
 
bool? CanSetRelationship(BasePlayer player, BasePlayer otherPlayer, RelationshipManager.RelationshipType relationshipType, int weight)
{
    Puts("CanSetRelationship works!");
    return null;
}

Entity Hooks
CanBradleyApcTarget
Called when an APC targets an entity
Returning true or false overrides default behavior
bool CanBradleyApcTarget(BradleyAPC apc, BaseEntity entity)
{
    Puts("CanBradleyApcTarget works!");
    return true;
}
OnNpcPlayerResume
Useful for canceling the invoke of TryForceToNavmesh
Returning a non-null value cancels default behavior
object OnNpcPlayerResume(NPCPlayerApex npc)
{
    Puts("OnNpcPlayerResume works!");
    return null;
}
object OnNpcStopMoving(NPCPlayerApex npc)
{
    Puts("OnNpcStopMoving works!");
    return null;
}
