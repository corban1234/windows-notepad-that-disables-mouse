# Create a temporary PowerShell script
$scriptPath = "$env:TEMP\disable_mouse.ps1"
@"
Add-Type -TypeDefinition @"
using System;
using System.Runtime.InteropServices;

public class MouseInput
{
    [DllImport("user32.dll")]
    public static extern bool BlockInput(bool fBlockIt);
}

"@

[MouseInput]::BlockInput($true)
Start-Sleep -Seconds 10
[MouseInput]::BlockInput($false)
"@ | Out-File -FilePath $scriptPath -Encoding ASCII

# Execute the PowerShell script
powershell.exe -ExecutionPolicy Bypass -File $scriptPath

# Delete the temporary script
Remove-Item -Path $scriptPath -Force
