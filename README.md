# Aggressor-Scripts
Aggressor scripts for Cobalt Strike

## UAC Bypass - Silent Cleanup
This is a cna for the silentcleanup UAC bypass that bypasses "always notify" aka the highest UAC setting, even on Windows 10 (1909) as of March 2020. You can find details [here](https://enigma0x3.net/2016/07/22/bypassing-uac-on-windows-10-using-disk-cleanup/).

This code uses [plaintext](https://github.com/juliourena/plaintext)'s C# port of the bypass, which can be found [here](https://github.com/juliourena/plaintext/blob/master/CSharp%20Tools/UAC%20Bypass/uac_bypass_silentcleanup.cs).

I modified the code a bit (line 45 or line 46, depending on whether a command is passed or an exe is passed as an arg). 

With the exe method (uac-silentcleanup-exe), powershell.exe is called along with Start-Process -NoNewWindow to attempt to hide any indication that a new program was launched.

With the command method (uac-silentcleanup-command), cmd.exe /c is used to pass a command string provided by the user.

Run it from CS with

    beacon > runasadmin uac-silentcleanup-exe c:\windows\temp\beacon.exe
    
    beacon > runasadmin uac-silentcleanup-command net user Jim.Lahey Liquor1 /add
