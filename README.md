### WeaponBuy
search string: `aItemPurchase ; "item_purchase"`

args: `TODO`

dll: server

![image](https://github.com/Salvatore-Als/cs2-signature-list/assets/58212852/b12fea36-db7d-441b-9280-111aafac94c6)

---

### GiveNamedItem
search string: `aNullptrEntInGi ; "nullptr Ent in GiveNamedItem: %s!`

args: `TODO`

dll: server

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

prototype: `void UTIL_SayTextFilter2(IRecipientFilter* filter, CBaseEntity* pEntity, bool chat, const char* msg_name, const char* param1, const char* param2, const char* param3, const char* param4);

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

prototype: `void UTIL_SayTextFilter2(IRecipientFilter* filter, const char* pText, CBasePlayerController* pPlayer, bool chat);`

---

### TeamChange
search string `"\"%s<%i><%s><%s>\" ChangeTeam() CTMDBG`

args: `CBasePlayerController *pController, int teamIndex`

dll: server

![image](https://github.com/Salvatore-Als/cs2-signature-list/assets/58212852/164f1a0e-73b8-48a6-a05e-8ac91c15177d)
