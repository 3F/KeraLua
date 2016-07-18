[ obsolete ]

This **KeraLua** - has been replaced on new **[LunaRoad](https://github.com/3F/LunaRoad)** !

*Use `master` branch if you search modifications for KeraLua*


## LunaRoad

Easy to start:

```csharp
using(var l = new Lua<ILua51>("Lua51.dll")) {
    // ...
}
```

Flexible binding with any exported function of library:

```csharp
// custom binding:
using(ILua l = new Lua("Lua52.dll")) {
    l.bind<Action<LuaState, LuaCFunction, int>>("pushcclosure")(L, onProc, 0);
    l.bind<Action<LuaState, string>>("setglobal")(L, "onKeyDown");
    //or any exported function like: bindFunc<...>("_full_name_")
    ...
    double num = l.bind<Func<LuaState, int, double>>("tonumber")(L, 7);
}

// API layer:
using(var l = new Lua<ILua53>("Lua53.dll")) {
    l.API.pushcclosure(L, onProc, 0); // ILua53 lua = l.API
    l.API.setglobal(L, "onKeyDown");
}
```

Powerful work with several libraries:

```csharp
using(var lSpec = new Lua("SpecLib.dll")) {
    using(ILua l = new Lua<ILua52>("Lua52.dll")) {
        //...
    }
}
```

Lazy loading:

```csharp
using(var l = new Lua<ILua51>(
                    new LuaConfig("Lua51.dll") {
                        LazyLoading = true
                    }))
{
    ...
}
```

[and more ...](https://github.com/3F/LunaRoad)

* https://github.com/3F/LunaRoad