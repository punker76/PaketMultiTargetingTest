# PaketMultiTargetingTests

## Excluding libraries in paket.references

[Excluding libraries](https://fsprojects.github.io/Paket/references-files.html#Excluding-libraries) doesn't work with the new csproj file system.

```
Costura.Fody content: once
JetBrains.Annotations
MahApps.Metro.IconPacks
MahApps.Metro
Caliburn.Micro
	exclude System.Windows.Interactivity

MaterialDesignThemes framework: >= net45
```

The `System.Windows.Interactivity.dll` should be exclude from `Caliburn.Micro` cause it's already in `ControlzEx` dependency of `MahApps.Metro`.

![2018-03-31_21h57_04](https://user-images.githubusercontent.com/658431/38167204-bad9ffe8-3531-11e8-91b3-cb9b2583cef3.png)

## framework restriction in paket.references

The `MaterialDesignThemes` package should only be add for >= .NET45

```
JetBrains.Annotations
MahApps.Metro.IconPacks
MahApps.Metro

MaterialDesignThemes framework: >= net45
```

Bu the `PaketMultiTargetingTest.csproj.net40.paket.resolved` contains also the `MaterialDesignThemes` package.

```
ControlzEx,3.0.2.4,Transitive,Main,false
JetBrains.Annotations,11.1,Direct,Main,false
MahApps.Metro,1.6.1,Direct,Main,false
MahApps.Metro.IconPacks,2.1,Direct,Main,false
MaterialDesignColors,1.1.3,Transitive,Main,false
MaterialDesignThemes,2.4.0.1044,Direct,Main,false
```

![2018-03-26_21h02_24](https://user-images.githubusercontent.com/658431/37927219-c58fd47c-3139-11e8-9770-46f33149c9f4.png)
