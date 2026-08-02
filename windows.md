# Windows

## Battery Report

Run on cmd

```bash
powercfg /batteryreport
```


## Ultimate Performance

Run on Powershell
```bash
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
```

Then open `Control Panel\All Control Panel Items\Power Options\Edit Plan Settings`, and you should be able to see `Ultimate Performance Power Plan`


## WSL Config to use same IP address as Windows Host

Create a file alled `.wslconfig` in `C:\Users\<YourUsername>\`

```text
[wsl2]
networkingMode=mirrored
dnsTunneling=true
firewall=true
autoProxy=true
```

Restart wsl
```bash
wsl --shutdown
wsl
```

