# Linux Host Computer Tips

Here are some tips an tricks related to the desktop/laptop linux host computer that you may use to connect to your NavQPlus.

{% hint style="warning" %}
Note that these tips and notes are NOT generic, and usually related to very specific releases or configurations. ensure you understand the notes and that they apply to your particular configuration.
{% endhint %}



## Ubuntu HOST laptop cannot screens share in MS Teams

Reported June 2023 - IAFG\
We often communicate, and have debug sessions using Microsoft Teams, (or Zoom).  During a session on Teams it is helpful to share the screen of the Ubuntu Host.&#x20;

Current Ubuntu distributions (22.04) may only enable Wayland graphics by default. However X is required in order for screensharing to work with TEAMs and ZOOM (possibly others).

_Depending on your LInux distribution you may be able to switch to X simply by logging out. Use the small gear icon in the lower right of the screen to then select Ubuntu using X._

Follow this guide to enabling  X on Ubuntu Linux to allow screen sharing:\
[https://askubuntu.com/questions/1405195/how-to-share-a-screen-in-ms-teams-or-zoom-from-ubuntu-22-04](https://askubuntu.com/questions/1405195/how-to-share-a-screen-in-ms-teams-or-zoom-from-ubuntu-22-04)

{% embed url="https://askubuntu.com/questions/1405195/how-to-share-a-screen-in-ms-teams-or-zoom-from-ubuntu-22-04" %}

Below is a copy of the instructions given in the link:

> **To disable Wayland and use xorg only:**
>
> 1. Open your terminal and write `sudoedit /etc/gdm3/custom.conf`
> 2. Uncomment the value `waylandEnabled=false` -- just remove the #
> 3. Press Ctrl+O then Enter then Ctrl+X
> 4. Reboot your computer.

