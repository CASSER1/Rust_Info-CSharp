# Init
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

Called when a server restart is being cancelled  
Returning a non-null value overrides default behavior

```c
object OnServerRestartInterrupt()
{
    Puts("OnServerRestartInterrupt works!");
    return null;
}
```
