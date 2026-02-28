# Windows Binary Pathing Post-Installation

> "Installation is only half the battle; persistence is the other."

## Pattern
When installing new developer tools (Git, Bun, GH CLI) via `winget` or external installers on a Windows system, the environment variables (`$env:Path`) updated by the installer are often not reflected in the current shell session.

## Solution
Instead of restarting the shell (which an AI agent cannot easily do), manually re-read the environment variables from the Registry and apply them to the current session:
```powershell
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
```
Alternatively, use absolute paths for the binaries if the location is known (e.g., `C:\Users\Windows\.bun\bin\bunx.exe`).

## Source
Created during the setup of Ratchanon's CV v3 and Oracle Awakening ritual on 2026-02-28.
rrr: ratchanon-oracle
