# Init
EN
1. Called when a plugin is being initialized  
2. Other plugins may or may not be present, dependant on load order  
3. No return behavior

RU
1. Вызывается при инициализации плагина  
2. Другие плагины могут присутствовать, а могут и не присутствовать, в зависимости от порядка загрузки  
3. Нет поведения возврата

```c
void Init()
{
    Puts("Init works!");
}
```
# OnServerRestartInterrupt
EN
1. Called when a server restart is being cancelled  
2. Returning a non-null value overrides default behavior

RU
1. Вызывается при отмене перезапуска сервера   
2. Возврат ненулевого значения переопределяет поведение по умолчанию

```c
object OnServerRestartInterrupt()
{
    Puts("OnServerRestartInterrupt works!");
    return null;
}
```

# OnServerShutdown
EN
1. Useful for saving something / etc on server shutdown  
2. No return behavior

RU
1. Полезно для сохранения чего-либо / etc при завершении работы сервера 
2. Нет поведения возврата

```c
void OnServerShutdown()
{
    Puts("OnServerShutdown works!");
}
```

# OnServerCommand
EN
1. Useful for intercepting commands before they get to their intended target
2. Returning a non-null value overrides default behavior

RU
1. Полезно для перехвата команд до того, как они достигнут намеченной цели  
2. Возврат ненулевого значения переопределяет поведение по умолчанию

```c
object OnServerCommand(ConsoleSystem.Arg arg)
{
    Puts("OnServerCommand works!");
    return null;
}
```

# OnMessagePlayer
EN
1. Useful for intercepting server messages before they get to their intended target  
2. Returning a non-null value overrides default behavior

RU
1. Полезно для перехвата сообщений сервера до того, как они попадут к намеченной цели  
2. Возврат ненулевого значения переопределяет поведение по умолчанию

```c
object OnMessagePlayer(string message, BasePlayer player)
{
    Puts("OnMessagePlayer works!");
    return null;
}
```

# onFrame
EN
1. Called each frame
2. No return behavior

RU
1. Вызывал каждый фрейм  
2. Нет поведения возврата

```c
void OnFrame()
{
    Puts("OnFrame works!");
}
```

# OnServerInformationUpdated
EN
1. Called after all steam information for the server has has been updated  
2. No return behavior

RU
1. Вызывается после обновления всей информации steam для сервера
2. Нет поведения возврата

```c
void OnServerInformationUpdated()
{
    Puts("OnServerInformationUpdated works!");
}
```

# OnRconCommand
EN
1. Called when an RCON command is run  
2. No return behavior

RU
1. Вызывается при выполнении команды RCON  
2. Нет поведения возврата

```c
void OnRconCommand(IPAddress ip, string command, string[] args)
{
    Puts("OnRconCommand works!");
}
```

# OnRconConnection
EN
1. Called when a new RCON connection is opened
2. Returning a non-null value overrides default behavior

RU
1. Вызывается при открытии нового соединения RCON
2. Возврат ненулевого значения переопределяет поведение по умолчанию

```c
object OnRconConnection(IPAddress ip)
{
    Puts("OnRconConnection works!");
    return null;
}
```

# OnPluginLoaded
EN
1. Called when any plugin has been loaded
2. No return behavior
3. Not to be confused with Loaded

RU
1. Вызывается при загрузке любого плагина  
2. Нет поведения возврата  
3. Не следует путать с Загружен

```c
void OnPluginLoaded(Plugin plugin)
{
    Puts($"Plugin '{plugin.Name}' has been loaded");
}
```

# OnNewSave
EN
1. Called when a new savefile is created (usually when map has wiped)
2. No return behavior

RU
1. Вызывается при создании нового файла сохранения (обычно после удаления карты)
2. Нет поведения возврата

```c
void OnNewSave(string filename)
{
  Puts("OnNewSave works!");
}
```

# OnPluginUnloaded
EN
1. Called when any plugin has been unloaded  
2. No return behavior  
3. Not to be confused with Unload

RU
1. Вызывается, когда какой-либо плагин был выгружен
2. Нет поведения возврата
3. Не следует путать с Выгружать

```c
void OnPluginUnloaded(Plugin plugin)
{
    Puts($"Plugin '{plugin.Name}' has been unloaded");
}
```

# OnServerMessage
EN
1. Called before a SERVER message is sent to a player
2. Return a non-null value to stop message from being sent

RU
1. Вызывается перед отправкой сообщения СЕРВЕРА игроку
2. Возвращает ненулевое значение, чтобы остановить отправку сообщения

```c
//  Example that stops message from being sent
//  Пример, который останавливает отправку сообщения

object OnServerMessage(string message, string playerName, string color, ulong playerId)
{
    if (message.Contains("gave"))
    {
        Puts($"Message to {playerName} ({playerId}) cancelled");
        return false;
    }

    return null;
}
```

# OnServerInitialized
EN
1. Called after the server startup has been completed and is awaiting connections  
2. Also called for plugins that are hotloaded while the server is already started running  
3. Boolean parameter, false if called on plugin hotload and true if called on server initialization
No return behavior

RU
1. Вызывается после завершения запуска сервера и ожидает подключения
2. Также вызывается для плагинов, которые загружаются горячим способом, когда сервер уже запущен
3. Логический параметр, false, если вызывается при горячей загрузке плагина, и true, если вызывается при инициализации сервера
Нет поведения возврата

```c
void OnServerInitialized(bool initial)
{
    Puts("OnServerInitialized works!");
}
```

# OnTick
EN
1. Called every tick (defined by the tick rate of the server)
2. For better performance, avoid using heavy calculations in this hook.
3. No return behavior

RU
1. Вызывается при каждом тике (определяется тактовой частотой сервера)  
2. Для повышения производительности избегайте использования сложных вычислений в этом хуке.  
3. Нет поведения возврата

```c
void OnTick()
{
    Puts("OnTick works!");
}
```

# OnServerSave
EN
1. Called before the server saves  
2. No return behavior

RU
1. Вызывается перед сохранением сервером  
Нет поведения возврата

```c
void OnServerSave()
{
    Puts("OnServerSave works!");
}
```

# OnServerSave
EN
1. Called before the server saves  
2. No return behavior

RU
1. Вызывается перед сохранением сервером  
Нет поведения возврата

```c
void OnServerSave()
{
    Puts("OnServerSave works!");
}
```


