# Bridge Scripts (Custom Scripts)

There are two ways of adding custom scripts to your `GameObject`s. The first is the simpler, and far less complicated method, which is to dynamically add the script to the `GameObject` on startup of your main patch. This method is preferred, but will not work if you need to edit variables of this script inside the Unity Editor. Think of it like the `Mast` script in the base-game, it has a variable called `Only Square Sails` that you might need to tick inside the editor. If your script is like this, move on to the next method.

The more complicated version, is to create a new Visual Studio project called `<Project>Bridge` replacing `<Project>` with whatever your main mod is called. In this new project you will create a script that extends `MonoBehaviour` like so:

```
namespace MyProjectBridge
{
    public class MyClass : MonoBehaviour
    {
        public GameObject variable;
    }
}
```

Now compile this .dll file, and copy it into a folder called `Scripts` inside your workspace in the Unity editor. Your mod folder in the Unity Editor should look something like this:

```
Assets
  \ My Mod
    \ Material
    \ Mesh
    \ Scripts
    \ Texture2D
```

You can add your custom scripts to your `GameObject`, then compile the `AssetBundle`.

Inside your main mod's code, you will need to load this new bridge file. I recommend doing this in the `FloatingOriginManager` patch, as this will occur at game launch. A simple check to ensure the file exists will prevent issues as well.

```
string path = Paths.PluginPath + "\\MyMod";

if (File.Exists(path + "\\MyModBridge.dll"))
{
  Assembly.LoadFrom(path + "\\MyModBridgde.dll");
}
```

Ensure that both your main mod and the bridge .dll file are in the same folder in the `Plugins` BepInEx folder. You will also need to create a new reference in your main mod to the .dll file of the bridge mod.
