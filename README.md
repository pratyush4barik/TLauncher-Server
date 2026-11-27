#  TLauncher-Server

A self-hosted Minecraft Java Edition multiplayer server built using PaperMC. Designed for college students and friends who want to play Minecraft together using TLauncher or other compatible Minecraft launchers over the same local Wi-Fi network.

**Just one computer hosting the server and friends connecting through the local network. No paid hosting required!**

---

##  REQUIREMENTS

- Windows 10 / Windows 11
- Java (version depends on your Minecraft server version)
- PaperMC Server Software
- Minecraft Java Edition / TLauncher
- Stable Wi-Fi connection
- Minimum 4GB RAM recommended for the host computer

---

#  SERVER SETUP GUIDE

## STEP - 1: Install Java

- Install the Java version required by your Minecraft server.
- https://java-for-minecraft.com/en/
- https://docs.aws.amazon.com/corretto/latest/corretto-25-ug/downloads-list.html
- https://corretto.aws/downloads/latest/amazon-corretto-25-x64-windows-jdk.msi - Direct Download Link
- Open CMD (Command Prompt).
- Execute the following command:

```cmd
java -version
```

- If Java is installed correctly, CMD will display the installed Java version.
- If Java is not recognized, install Java or configure your PATH environment variable.

---

## STEP - 2: Create a Server Folder

- Go to your Desktop.
- Right-click → New → Folder.
- Name the folder:

```text
TLauncher-Server
```

- This folder will contain all your Minecraft server files.

---

## STEP - 3: Download Minecraft Server Software (PaperMC)

We are using PaperMC because it offers better performance and plugin support compared to the standard Minecraft server.

**PaperMC Downloads:**

https://papermc.io/downloads/paper

Instructions:

- Select Minecraft Java Edition.
- Select your preferred Minecraft version.
- Download the latest stable build.
- Move the downloaded `.jar` file into your server folder.
- Rename the file:

```text
paper.jar
```

---

## STEP - 4: Create a Startup File

The startup file will automatically launch your Minecraft server.

Instructions:

- Open your `TLauncher-Server` folder.
- Right-click → New → Text Document.
- Rename the file:

```text
start.bat
```

**COMMON ERROR:** Make sure the filename doesn't become `start.bat.txt`.

- Open the file using Notepad.
- Enable file extension from folders view option.
- Paste the following code:

```bat
@echo off
title College Minecraft Server

java -Xms2G -Xmx4G -jar paper.jar --nogui

pause
```

- Save the file.
- Remove --nogui if u need the ram usage interface.
- Double-click `start.bat` to launch the server.

**What does this code do?**

- `@echo off` – Hides unnecessary command output.
- `title` – Sets the CMD window title.
- `-Xms2G` – Allocates a minimum of 2GB RAM.
- `-Xmx4G` – Allocates a maximum of 4GB RAM.
- `--nogui` – Runs the server without a graphical interface.
- `pause` – Keeps the command window open after execution.

**NOTE:** The first time you launch the server, it will generate configuration files and stop because you haven't accepted the Minecraft EULA.

---

## STEP - 5: Accept Minecraft EULA

- Open your server folder.
- Find the file:

```text
eula.txt
```

- Open it using Notepad.
- Find:

```properties
eula=false
```

- Change it to:

```properties
eula=true
```

- Save the file.

**NOTE:** Only change this setting after reading and agreeing to the Minecraft EULA.

---

## STEP - 6: Start the Minecraft Server

- Double-click `start.bat` again.
- Wait for the server to generate the world and load all necessary files.
- Once the console displays:

```text
Done! For help, type "help"
```

Your Minecraft server is successfully running!

---

## STEP - 7: Configure TLauncher Compatibility

By default, Minecraft servers authenticate players using official Minecraft accounts.

To allow compatible offline-mode clients, we need to modify the server configuration.

Instructions:

- Open your server folder.
- Find:

```text
server.properties
```

- Open it using Notepad.
- Find the following setting:

```properties
online-mode=true
```

- Change it to:

```properties
online-mode=false
```

Also configure the following settings:

```properties
server-port=25565
server-ip=
online-mode=false
gamemode=survival
difficulty=normal
max-players=20
pvp=true
spawn-protection=0
view-distance=8
simulation-distance=6
```

- Save the file.
- Go to the server console.
- Type:

```text
stop
```

- Restart the server using `start.bat`.

**IMPORTANT SECURITY WARNING:**

Offline mode disables official Minecraft account authentication. Players can impersonate other usernames, including administrator usernames.

For a private server:
- Never expose the server publicly.
- Use a suitable authentication plugin.
- Restrict server access to trusted devices.
- Never give OP permissions to unknown players.

---

# 🌐 CONNECT THROUGH COLLEGE WI-FI

## STEP - 8: Find Your Local IP Address

Your computer is now hosting the Minecraft server. Other players need your local IP address to connect.

Instructions:

- Press `Win + R`.
- Type `cmd`.
- Press Enter.
- Execute:

```cmd
ipconfig
```

- Find the section:

```text
Wireless LAN adapter Wi-Fi
```

- Look for:

```text
IPv4 Address
```

Example:

```text
IPv4 Address: 192.168.1.105
```

Your local IP address will be different.

**IMPORTANT:** Share this IP address with your friends. Do not share your public IP address.

---

## STEP - 9: Configure Windows Firewall

Windows Firewall may block incoming Minecraft connections.

Instructions:

- Search for Windows Defender Firewall.
- Open Advanced Settings.
- Select Inbound Rules.
- Click New Rule.
- Select Port.
- Choose TCP.
- Enter:

```text
25565
```

- Select Allow the connection.
- Apply the appropriate network profile.
- Name the rule:

```text
Minecraft Server
```

- Finish the setup.

Make sure Java is also allowed through the firewall on the appropriate network profile.

**NOTE:** Do not disable Windows Firewall completely.

---

## STEP - 10: Connect Friends to Your Server

Now your friends can join your Minecraft world!

Instructions for other players:

1. Connect to the same college Wi-Fi.
2. Open TLauncher.
3. Select the same Minecraft version as the server.
4. Launch Minecraft.
5. Open Multiplayer.
6. Click Add Server.
7. Enter the following address:

```text
YOUR_LOCAL_IP:25565
```

Example:

```text
192.168.1.105:25565
```

8. Click Done.
9. Select your server.
10. Click Join Server.

**Congratulations! Your friends can now play together in the same Minecraft world.**

---

# 🔧 TROUBLESHOOTING

## Problem 1: Connection Timed Out

Possible reasons:

- Windows Firewall is blocking the connection.
- The server is not running.
- Incorrect local IP address.
- College Wi-Fi has client isolation enabled.

Solution:

Check whether your server is running and verify the IP address.

Ask another player to execute:

```powershell
Test-NetConnection YOUR_SERVER_IP -Port 25565
```

Example:

```powershell
Test-NetConnection 192.168.1.105 -Port 25565
```

Look for:

```text
TcpTestSucceeded : True
```

If it returns `False`, check the firewall and network configuration.

---

## Problem 2: Incompatible Version

Possible reason:

- The player's Minecraft version doesn't match the server version.

Solution:

Make sure everyone selects the same Minecraft version.

---

## Problem 3: Failed to Verify Username

Possible reason:

- The server is still running in online mode.

Solution:

- Open `server.properties`.
- Verify:

```properties
online-mode=false
```

- Restart the server.

---

## Problem 4: Server Not Starting

Possible reasons:

- Incorrect Java version.
- Java is not installed properly.
- Incorrect `.jar` filename.
- Insufficient RAM.

Solution:

Check Java:

```cmd
java -version
```

Verify that your server folder contains:

```text
TLauncher-Server/
│
├── paper.jar
├── start.bat
├── eula.txt
└── server.properties
```

---

# ⚠️ IMPORTANT: COLLEGE WI-FI RESTRICTIONS

Being connected to the same Wi-Fi network does not guarantee that devices can communicate with each other.

Some college networks use:

- AP Isolation
- Client Isolation
- VLAN Segmentation
- Firewall Restrictions

These settings may prevent players from connecting to your server.

If the connection fails even after configuring everything correctly, contact your college network administrator and request permission for local device-to-device communication on TCP port `25565`.

Do not attempt to bypass your college's network restrictions.

---

# 🎯 FUTURE IMPROVEMENTS

Features that can be added to this server:

- [ ] Custom Minecraft world
- [ ] Player authentication
- [ ] Land protection
- [ ] Anti-griefing plugins
- [ ] Economy system
- [ ] Player shops
- [ ] Home and teleport commands
- [ ] Automatic world backups
- [ ] Server status dashboard
- [ ] Player statistics

---

#  PROJECT INFORMATION

**Project Name:** TLauncher-Server

**Server Software:** PaperMC

**Platform:** Windows

**Game:** Minecraft Java Edition

**Network:** Local Area Network (LAN)

**Default Port:** 25565

**Hosting:** Self-hosted

**Cost:** No paid hosting required.

---

###  Support the Project

If this guide helped you create your own Minecraft server, consider giving this repository a ⭐ on GitHub!

**One Server. One World. Endless Adventures.**
