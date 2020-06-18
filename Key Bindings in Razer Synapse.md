<h1>Key Bindings in Razer Synapse</h1>



---

This guide is intended for the Razer Orbweaver Chroma, although it should work on other Razer products.

Orbweaver Chroma Specs:
* 20 mechanical keys
* 8 direction joypad
* 2 thumb buttons
* 8 keymaps giving a total of 240 different key combinations

---

0. Install Razer Synapse if not done already
1. Open Razer Synapse and navigate to `Keypad>Customize`
2. Select the profile you want to use, or just use the default one named `Profile`
3. Select the key you want to modify
4. Select the `Button Assignment` from the list below:

|Name|Description|
|---|---|
|Keyboard Function|When pressed, executes a single key press, or key combination|
|Mouse Function|When pressed, executes the selected mouse function (left click, right click, etc)|
|Macro|When pressed, executes a Macro (can be repeated)|
|Inter-Device|
|Switch Keymap|When pressed, either switches to a specific keymap, or cycles through keymaps|
|Switch Profile|When pressed, switches profile to the specified profile|
|Launch Program|When pressed, launches a program (.bat, .exe, .vbs, etc), or opens a website in your **default browser**|
|Joystick|When pressed, executes the defined joystick button|
|Multimedia|When pressed, executes multimedia functions such as play, pause, forward, backward, volume up and down|
|Windows 8 Charms|When pressed, executes the specified action such as cycling through apps, snapping apps, opening settings, etc|
|Windows Shortcuts|When pressed, executes the specified action such as launching Task Manager, cycling apps, copy and paste, etc
|Disable|Disables the key and does nothing on key press|

---

<h2>Examples:</h2>

**Note: Razer Synapse seems to not like launching shortcuts, so it is best to find the `.exe` of the application you want to launch and set Synapse to open that instead**

<h4>1. Launching the file browser to a specific folder:</h4>

1. Create a batch file named however you want
2. Inside the batch file add these two lines, replacing the location of the folder with the one you wish to open
    *    ```
            @echo off
            explorer "C:\Users\Wally\Downloads"
    * This also works for network locations by setting the location as the IP or hostname with `\\hostname\share`
3. Save the batch file
4. Go to Razer Synapse, and set a key to `Launch Program`
5. Select the batch file you created
6. When you press that key, the batch file should run and it will open the folder as specified

<br>
<br>
<h4>2. Opening a Windows App</h4>

*This is for opening a Windows App, not a program. An App is the application you would download from the Windows Store.*

The reason why we need to go through all these steps, is we cannot access the Application path at `C:\Program Files\WindowsApps`. **Do not change the security or permissions for this folder or you may break Windows.**

1. We will need to find the application executable location
2. Open Run and type `shell:appsfolder` to open the Applications folder
3. Find the app you want to have Razer open
4. Right click on the app, and click `Create Shortcut`
    * If it asks to be placed on the desktop, select `Yes`
5. Find the shortcut on the Desktop, right click it and go to `Properties`
6. Take note of the `Target type` as that is what we will be looking for
7. Open a Powershell shell
    * We will now output all AppXPackages currently installed to a text file so we can search that text file for the one we want
8. In Powershell, run `get-appxpackage > 123.txt`
9. Run `notepad.exe 123.txt` to open the file
10. In that text file, press `Control+F` to open a search box
11. Search for the `Target Type` of the shortcut you made in step 4
    * You are searching for the `Target Type`
    * You are looking for the `PackageFullName` that matches the `Target Type`
12. Once you find the proper target type, copy the `InstallLocation` and navigate to it in your File Browser
13. The executable of the Windows App you want to open should be in this folder
14. Create a batch file with the second line being the path to the executable of the Windows App
```
    @echo off
    "C:\Path\To\App.exe"
```
15. Save the batch file
16. Set Synapse to open that batch file, which will then launch the Windows App