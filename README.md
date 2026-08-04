```diff
+ 29 july 2026
+ new build system seems to be working great for both x64 and arm64.
+ I'd like to understand if it's possible for me to codesign Airplay_Engine before making a new release
```

# FREE AirPlay to your Windows PC
Free as both in "freedom" and "free beer"!

## Installation
Download the latest version of Airplay_Engine from [**releases**](https://github.com/leapbtw/Airplay_Engine/releases/latest).

After installing, control Airplay_Engine from it's [tray icon](https://www.odu.edu/sites/default/files/documents/win10-system-tray.pdf)! Right-click it to start or stop AirPlay. \
You can also set it to run automatically when your PC starts

## FAQ — Please Read!
> [!NOTE]
> *What is Airplay_Engine?*
> 
> [Airplay_Engine](.) is a software that allows you to video stream with AirPlay to your windows PC. \
> It turns [UxPlay](https://github.com/FDH2/UxPlay/) into a fully featured App for Windows 10/11 users, making it easier for those who may find compiling UxPlay challenging.
> 
> Most other software achieving the same functionality as `Airplay_Engine` is usually paid and non-free.


> [!TIP]
> *My \<apple device\> can't connect to my PC!!!*
> 1. Check if the `Airplay_Engine.exe` is running: right-click the tray icon and restart it.
> 2. Toggle Wi-Fi and Bluetooth OFF on your iPhone/iPad/Mac, wait a couple of seconds and reconnect. It might take a few attempts.
> 3. As last resort, close Airplay_Engine, open Task Manager and restart `Bonjour Service` from the Services tab. Then reopen Airplay_Engine and try again

> [!IMPORTANT]
> *Why is Windows Defender complaining during installation?*
> 
> ![alt text](https://raw.githubusercontent.com/leapbtw/Airplay_Engine/refs/heads/x64/stuff/defender.png "defender")
>
> Just click on `More info` and it will let you install. It complains because the executable is not signed. If you don't trust this software you can always build it yourself! See below.
>
> If prompted by Windows Firewall, please **allow** Airplay_Engine to ensure it functions properly.


> [!NOTE]
>  *How do I build this software myself?*
> 
> Please see [BUILDING.md](./docs/BUILDING.md)
<br>

<details>
<summary><strong>Advanced configuration</strong></summary>

<br>

UxPlay arguments are read from `arguments.txt`.

Configuration precedence:

1. `%ProgramData%\Airplay_Engine\arguments.txt`
2. `%APPDATA%\leapbtw\Airplay_Engine\arguments.txt`
3. built-in default: `-n Airplay_Engine -nh`

The machine-wide file takes precedence when it exists, allowing administrators
to enforce a shared configuration. When it is absent, each user can maintain
their own configuration under `%APPDATA%`.

Environment variables are expanded when the app starts. For example:

```text
-n %COMPUTERNAME% -nh
```

</details>

<details>
<summary><strong>Local x64 development</strong></summary>

<br>

After installing MSYS2, the complete local build is one PowerShell command:

```powershell
.\build.ps1 package
```

It produces a verified portable ZIP and MSI under `out\x64\artifacts`. See the
[developer guide](./docs/DEVELOPERS-GUIDE.md) for prerequisites and additional
commands.

</details>

<details>
<summary><strong>TODO</strong></summary>

<br>

- make an update checker

</details>

<details>
<summary><strong>Known Issues</strong></summary>

<br>

~~uxplay bugs out when waking PC from Sleep~~
~~you can fix this by killing Airplay_Engine.exe and restarting Bonjour Service, and restarting uxplay.exe. Also restarting your PC might fix this.~~  \
Apparently moving from Bonjour PS to mDNSResponder fixed it? :)

</details>

## Reporting Issues
Please report issues related to the build system created with GitHub Actions in this repository. For issues related to other parts of this software, report them in their respective repositories.

## License
Please take a look at the [LICENSE](./docs/LICENSE.rtf).
