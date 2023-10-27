search string: `#Cstrike_Name_Change`, and xref

```cpp
UTIL_SayTextFilter2((__int64)&v45, v14, 1, (__int64)"#Cstrike_Name_Change", v10, &v51, 0i64, 0i64);
v15 = (__int64 *)(*(__int64 (__fastcall **)(__int64, const char *, _QWORD, _QWORD))(*(_QWORD *)g_pGameEventManager + 48i64))(
                    g_pGameEventManager,
                    "player_changename",
                    0i64,
                    0i64);
```

prototype: `void UTIL_SayTextFilter2(IRecipientFilter* filter, CBaseEntity* pEntity, bool chat, const char* msg_name, const char* param1, const char* param2, const char* param3, const char* param4)`

dll: `server`
