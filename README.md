This repository gives you indications on the strings to search in order to find the signatures of the functions on CS2.

Keep in mind that you will need to refine your search, it is not an exact science.

---

### WeaponBuy
search string: `aItemPurchase ; "item_purchase"`

args: `TODO`

dll: `server`

![image](https://github.com/Salvatore-Als/cs2-signature-list/assets/58212852/b12fea36-db7d-441b-9280-111aafac94c6)

---

### GiveNamedItem
search string: `aNullptrEntInGi ; "nullptr Ent in GiveNamedItem: %s!`

args: `TODO`

dll: `server`

You have to look for the one that contains kevlar and other indication in the function

![image](https://github.com/Salvatore-Als/cs2-signature-list/assets/58212852/926e26df-2156-4d1c-8b2d-640c20c41c91)

---

### UTIL_SayTextFilter2
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

---

### UTIL_SayTextFilter
xref `UTIL_SayTextFilter2`, look for the following snippet:

```cpp
if ( v59 )
{
    UTIL_SayTextFilter2((__int64)&v61, (__int64)v8, 1, v59, v19, v12, v60, 0i64);
}
else
{
    LOBYTE(v42) = 1;
    UTIL_SayTextFilter(&v61, v73, v8, v42);
}
```

prototype: `void UTIL_SayTextFilter2(IRecipientFilter* filter, const char* pText, CBasePlayerController* pPlayer, bool chat)`

dll: `server`

---

### CBasePlayerController::ChangeTeam
search string `"\"%s<%i><%s><%s>\" ChangeTeam() CTMDBG`

args: `CBasePlayerController *pController, int teamIndex`

dll: `server`

![image](https://github.com/Salvatore-Als/cs2-signature-list/assets/58212852/164f1a0e-73b8-48a6-a05e-8ac91c15177d)

---

### CBasePlayerController::HandleCommand_JoinTeam
search string `CBasePlayerController::HandleCommand_JoinTeam( %d ) - invalid team index.\n`

prototype: `bool CBasePlayerController::HandleCommand_JoinTeam(CBasePlayerController *pPlayerController, int teamIndex, bool bQueue)`

dll: `server`

---

### CCSPlayerController::SwitchTeam
search string `CCSPlayerPawnBase::SwitchTeam( %d ) - invalid team index.\n`

or search string `\"%s<%i><%s><%s>\" SwitchTeam => ChangeBasePlayerTeamAndPendingTeam =%d , req team %d %.2f \n`

prototype: `bool CCSPlayerController::SwitchTeam(CBasePlayerController *pPlayerController, int teamIndex)`

dll: `server`

---

### CGameRules::ClientSettingsChanged
search string `fov_desired`, xref

look for the following snippet:
```cpp
if ( (_DWORD)PlayerInfo != -1 )
    v4 = (_DWORD)PlayerInfo - 1;
  v31 = (_BYTE *)v30(g_Source2EngineToServer, v4, "fov_desired");
```

the current function is `CGameRules::ClientSettingsChanged`

prototype: `bool CGameRules::ClientSettingsChanged(CGameRules *pGameRules, CBasePlayerController *pPlayerController)`

dll: `server`

---

### GetCSGlobalTeam & UTIL_ConsolePrint
search string `%sTeam playing \"CT\": %s\n`

look for the following snippet:
```cpp
  if ( a1 )
    v2 = a1;
  v4 = GetCSGlobalTeam(3);
  if ( v4 )
  {
    v5 = (_BYTE *)sub_18014F360(v4);
    if ( v5 && *v5 )
    {
      UTIL_ConsolePrint("%sTeam playing \"CT\": %s\n", v2, v5);
    }
    else if ( v3 )
    {
      UTIL_ConsolePrint("%sTeam \"CT\" is unset.\n", v2);
    }
  }
```

prototype: `CCSTeam *GetCSGlobalTeam(int teamIndex)`

prototype: `void UTIL_ConsolePrint(const char *fmt, ...)`

dll: `server`

---

### UTIL_GetListenServerHost & UTIL_PlayerSlotToPlayerController
search string `UTIL_GetListenServerHost() called from a dedicated server or single-player game.\n`

look for the following snippet:
```cpp
__int64 UTIL_GetListenServerHost()
{
  __int64 v0; // rdx
  __int64 v1; // r8

  if ( !(unsigned __int8)sub_180CFAA80() )
    return UTIL_PlayerSlotToPlayerController(0);
  Warning("UTIL_GetListenServerHost() called from a dedicated server or single-player game.\n", v0, v1);
  return 0i64;
}
```

prototype: `CBasePlayerController *UTIL_GetListenServerHost()`

prototype: `CBasePlayerController *UTIL_PlayerSlotToPlayerController(CPlayerSlot slot)`

dll: `server`

---

### TakeDamage
search string `CBaseEntity::TakeDamageOld:`

prototype: `void TakeDamage(CBaseEntity *pVictim, CTakeDamageInfo *damageInfo)`

dll: `server`

![image](https://github.com/Salvatore-Als/cs2-signature-list/assets/58212852/1a17e82b-d276-4ee5-8e86-73e1665da4b4)

