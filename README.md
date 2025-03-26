# Ultimate Windows Cleanup & Optimization Script

## 📌 How to Use:
1. Open **Notepad**.
2. Copy and paste the code below.
3. Save it as **`clean_optimize_windows.bat`** (**Make sure it's `.bat`, not `.txt`**).
4. **Right-click** the file and select **"Run as Administrator"**.

---

## 🖥 Windows Cleanup & Optimization Script
```batch
@echo off
title Windows Cleanup & Optimization
echo Cleaning and optimizing Windows... Please wait.
echo.

:: Delete temporary files
echo Deleting temporary files...
del /s /f /q %temp%\* >nul 2>&1
del /s /f /q C:\Windows\Temp\* >nul 2>&1
del /s /f /q C:\Windows\Prefetch\* >nul 2>&1
echo Temporary files deleted.
echo.

:: Flush DNS cache
echo Flushing DNS cache...
ipconfig /flushdns
echo DNS cache flushed.
echo.

:: Check and fix disk errors
echo Checking disk for errors...
chkdsk C: /f /r /x
echo Disk check completed.
echo.

:: Free up RAM by clearing clipboard
echo Clearing clipboard...
echo off | clip
echo Clipboard cleared.
echo.

:: Run Disk Cleanup
echo Running Disk Cleanup...
cleanmgr /sagerun:1
echo Disk Cleanup completed.
echo.

:: Reset network settings
echo Resetting network settings...
netsh int ip reset >nul 2>&1
netsh winsock reset >nul 2>&1
echo Network settings reset.
echo.

:: Scan and repair system files
echo Running System File Checker (SFC)...
sfc /scannow
echo System scan completed.
echo.

:: Restore Windows health using DISM
echo Running DISM to restore system health...
DISM /online /cleanup-image /restorehealth
echo Windows health restored.
echo.

:: Clear Windows Event Logs
echo Clearing Windows Event Logs...
wevtutil cl Application >nul 2>&1
wevtutil cl Security >nul 2>&1
wevtutil cl System >nul 2>&1
echo Event logs cleared.
echo.

:: Remove old Windows updates
echo Cleaning up old Windows updates...
Dism /Online /Cleanup-Image /StartComponentCleanup /ResetBase
echo Old Windows updates removed.
echo.

:: Disable hibernation
echo Disabling hibernation...
powercfg -h off
echo Hibernation disabled.
echo.

:: Optimize and defragment drives
echo Optimizing drives...
defrag C: /O
echo Drive optimization completed.
echo.

echo Windows cleanup and optimization completed successfully!
pause
exit

✅ What This Script Does:
✔ Deletes temporary files from %temp%, C:\Windows\Temp, and C:\Windows\Prefetch.
✔ Flushes DNS cache to fix internet issues.
✔ Checks and fixes disk errors with chkdsk.
✔ Clears the clipboard to free up RAM.
✔ Runs Disk Cleanup to remove unnecessary files.
✔ Resets network settings to fix connection problems.
✔ Scans and repairs system files with sfc /scannow.
✔ Restores Windows health using DISM /restorehealth.
✔ Clears Windows event logs to free up space.
✔ Removes old Windows updates to reduce disk usage.
✔ Disables hibernation to free gigabytes of storage.
✔ Optimizes SSD & defragments HDD for better performance.
