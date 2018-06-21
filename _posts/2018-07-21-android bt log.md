---
layout: post
category: "android"
title: "android bt log"
tags: ["android"]
---

```python
#!/usr/bin/python

import re
import sys

dic = {
"avrcp":
    [
        "MediaController metadata changed", 
        "Active sessions changed", 
        "setVolumeNative",
        "active_stream_changed",
        "Send key",
        "Avrcp   : Updated"
    ],
"bond":
    [
        "btif_storage_load_bonded_devices", 
        "btif_dm_start_discovery",
        "btm_sec_disconnected sec_req:",
        "btm_ble_connected"
    ],
"opp":
    [
        "insertShare parsed URI"
    ],
"other":
    [
        "EventHub: New device"
    ]
}

def putDic():
    for k,v in dic.items():
        for i in v:
            print k,i
def searchDic():
    with open(sys.argv[1],'r+')as fileone:  
        for line in fileone.readlines(): 
            line = line.strip()
            for k, v in dic.items():
                for i in v:
                    if re.search(i, line, re.I):
                        print line+":::"+"\033[1;31m"+k+"\033[0m"
if __name__ == '__main__':  
    #putDic()  
    searchDic()           

```


