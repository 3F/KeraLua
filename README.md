[ obsolete ]

**KeraLua** - has been replaced on new **[LunaRoad](https://github.com/3F/LunaRoad)** !

*Use `master` branch if you need modifications for KeraLua*


----

**[LunaRoad](https://github.com/3F/LunaRoad)** represents a fully new flexible platform to work with Lua. Works via powerful **[Conari](https://github.com/3F/Conari) engine** !

[![Build status](https://ci.appveyor.com/api/projects/status/94y78phdvkoi5oda/branch/master?svg=true)](https://ci.appveyor.com/project/3Fs/lunaroad/branch/master)
[![NuGet package](https://img.shields.io/nuget/v/LunaRoad.svg)](https://www.nuget.org/packages/LunaRoad/) 
[![License](https://img.shields.io/badge/License-MIT-74A5C2.svg)](https://github.com/3F/LunaRoad/blob/master/LICENSE)


**Easy to start**:

```csharp
using(var l = new Lua<ILua51>("Lua.dll")) { 
    // ... 
    // ILua51, ILua52, ILua53, ...
}
```

Flexible binding with any exported function of library:

* **Dynamic features / DLR:**

*It does not require API level at all, we will generate all this* ***automatically at runtime*** ! *Easy and works well.*

```csharp
// all this will be generated at runtime, i.e. you can use all of what you need from Lua as you like:
dlr.pushcclosure(L, onProc, 0);
dlr.setglobal(L, "onKeyDown");
...
LuaNumber num = dlr.tonumber<LuaNumber>(L, 7);
```

* **Lambda expressions:**

```csharp
// custom binding:
using(ILua l = new Lua("Lua52.dll"))
{
    l.bind<Action<LuaState, LuaCFunction, int>>("pushcclosure")(L, onProc, 0);
    l.bind<Action<LuaState, string>>("setglobal")(L, "onKeyDown");
    //or any exported function like: bindFunc<...>("_full_name_")
    ...
    LuaNumber num = l.bind<Func<LuaState, int, LuaNumber>>("tonumber")(L, 7);
}

// API layer:
using(var l = new Lua<ILua53>("Lua53.dll"))
{
    l.API.pushcclosure(L, onProc, 0); // ILua53 lua = l.API
    l.API.setglobal(L, "onKeyDown");
}
```

*Since the LunaRoad works over [Conari](https://github.com/3F/Conari), it also does not require the creation of any additional* ***delegate***. *We'll do it* ***automatically*** *instead of you.* [[?](https://github.com/3F/LunaRoad/wiki/API)]

[and more ...](https://github.com/3F/LunaRoad)

* https://github.com/3F/LunaRoad

Enjoy.