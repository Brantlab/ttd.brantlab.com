+++
#archetype = "chapter"
title = "3. Setting up TTD"
weight = 3
+++

Upon getting the script in place we will want to attach our powershell script. 

 Get into the interface for TwoToneDetect and go to your tone configuration
Depending upon which version of powershell is installed on your system will depend on which version of this command you will want to use. 

To tell which powershell you have open powershell and type `$PSVersionTable`

You will have a result like this 
``` powershell
Name                           Value
----                           -----
PSVersion                      5.1.19041.3693
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.3693
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```
In this example I have version 5

If powershell 5 or later use `powershell "C:\TwoToneDetect73g\WhatYoudLike.ps1" -Des "[d]" -Time [t] -mp3 [mp3]`

If powershell 6 or later use `pwsh "C:\TwoToneDetect73g\WhatYoudLike.ps1" -Des "[d]" -Time [t] -mp3 [mp3]`

Some notes on both commands

1. Be sure your `"C:\TwoToneDetect73g\WhatYoudLike.ps1"` is the correct path for your instance. 
2. The `-Des "[d]" -Time [t] -mp3 [mp3]` are parameters that will be automatically filled in by TwoToneDetect
3. You need to have your execution policy set for your system to allow the scripts to run.
    * This is where things could be tricky. Depending on if this is a shared system or dedicated. [Here is a link with the help docs for it](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.4). 
    * If this is a shared system I would do remotesigned and bypass the scripts as noted in the help article
    * If this is a dedicated system to twotonedetect I would set unrestricted and the risk is relatively small.  

Once you have your command select go ahead and paste it in the post-email command box and save your tones config. 

