+++
#archetype = "chapter"
title = "2. Powershell Code"
weight = 2
+++
Some pre-requesits for this code. This makes the assumtion you have a FTP site you dump your audio onto so when the pushover is sent it has a link for you to go to listen to the audio on. 

Some fields of note for the codr you will need to change for your setup. 

`"<Your base url>"` should be formatted somethings like `"https://dispatch.brantlab.com/"` 
<br>
Be sure to include that last `/`. If your FTP dumps on `<site>/audio/whatever.mp3` then it shhould be something like `"https://dispatch.brantlab.com/audio/"`

`"<APP-TOKEN>"` Should be changed to your token like so `"axtzfru5##########17vcejpmnwv6"`<br><br>
`"<USER-TOKEN>"` Should be changed to your token like so `"tyuifru5##########17vcejpmnwv6"`
<br>

Sound is controlled by the sound field `sound = "Alarm_custom";` You can upload custom audio to the portal and control is here. Remove this field if you don't plan to use it. If you do use it make sure you change `Alarm_custom` to whatever audio file you uploaded. It is case sensative. 

Priority filed is adjusted using `priority = "1";` Please use -2, -1, 0, or 1 for this as outlined [here](https://pushover.net/api#priority). You can use 2 but it will require additonal parameters not currently in the scope of this project. 


``` powershell
param ($Des, $Time, $mp3)

$filename = split-path $mp3 -leaf
$domain = "<Your base url>" #Example https://dispatch.brantlab.com/
$Url = $domain + $filename

# This header tells we're passing a JSON payload

## PUSHOVER
$data = @{
    token = "<APP-TOKEN>";
    message = "Dispatched at $time";
    title = "$des Fire Department";
    url = "$url";
    priority = "1";
    url_title = "Audio Link";
    user = "<USER-TOKEN>";
    sound = "Alarm_custom";
}
Invoke-RestMethod -Method Post -Uri "https://api.pushover.net/1/messages.json" -Body $data | Out-Null
```

Once you have made the required changes save this file as `WhatYoudLike.ps1` at the root of your TwoToneDetect37(G) folder for easy access for TwoToneDetect software. 

## Testing this code
You can launch powershell and CD(Change Directory) to where this PS1 resides. 
<br>I.E. You can `CD C:\TwoToneDetect73g` if that is where your folder resides. 
<br> You can then type into powershell and press enter
<br>
``` powershell
.\WhatYoudLike.ps1 -des "Test" -Time "00:00:00" -mp3 test.mp3
```
This will send a pushover to your application and if signed in on the phone and apart of that app you will recieve a notice. 

![Powershell Testing GIF](/imgs/PS_test.gif)