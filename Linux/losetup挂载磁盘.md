### Examples
列出所有loop设备并有详细信息  
`losetup -a`  
把一个文件附加到loop设备  
`sudo losetup /dev/${loopN} ${file}`  
把一个文件附加到loop设备（只读）  
`sudo losetup --read-only /dev/${loopN} ${file}`  
Detach所有attached的设备  
`sudo losetup -D`  
Detach指定设备  
`sudo losetup -d /dev/${loopN}`  