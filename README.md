# Lenovo-R720-macOS
Install macOS High Sierra 10.13.4 on Lenovo Laptop R720

#My R720
i7-7700hq 
gtx1050 2g 
bcm94352z WiFi and Bluetooth

首先下载[黑果小兵的199版本镜像](https://blog.daliansky.net/macOS-High-Sierra-10.13.4-17E199-Release-Version-and-Clover-4418-Original-Image.html)，用transmac烧写镜像，这个时候直接安装可能会出现禁止符，确定放入GenericUSBXHCI.kext和USBInjectAll.kext（后者一般都有），然后U盘插2.0的口，开始安装。

安装完成后的状态是：显卡驱动，不能亮度，网卡驱动完美，声卡没驱动，USB3.0不能用（插鼠标能用），小键盘未驱动

将EFI转移到硬盘以后，加入ApplePS2SmartTouchPad解决小键盘问题，安装VoodooHDA285.pkg解决声卡问题

USB3.0使用如下kext patch解决


```
<dict>
                <key>Comment</key>
                <string>USB 10.13.4+ by PMHeart</string>
                <key>Disabled</key>
                <false/>
                <key>Find</key>
                <data>
                g32UDw+DlwQAAA==
                </data>
                <key>InfoPlistPatch</key>
                <false/>
                <key>MatchOS</key>
                <string>10.13.x</string>
                <key>Name</key>
                <string>com.apple.driver.usb.AppleUSBXHCI</string>
                <key>Replace</key>
                <data>
                g32UD5CQkJCQkA==
                </data>
            </dict>
```

出自 http://bbs.pcbeta.com/forum.php?mod=viewthread&tid=1782500


