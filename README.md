![Project Logo](assets/logo.png)

# Wifi Pineapple Cloner v4

The Pineapple NANO and TETRA are excellent security hardware but in 2020 they reached their end of life.<br>
So to give a new life to this platform on modern hardware I developed these scripts to port it to different routers.<br>

Sometime between 2019 and 2020 we started using the private beta of this project which my friends called "Pineapple Termidor".<br>
So at the time of redoing this project I decided to rescue the original name from forgotten 🤣


## About this project

This project is the result of everything I've experienced from 2018 to 2022 to successfully port the NANO and TETRA in any hardware.<br>

For this I've develop:
* The method of patching the file system with the minimum to be able to work. For this I created the list of files to copy and the script that copies them.
* A script to patch the file system to work on any hardware.
* Completely updated [panel](https://github.com/xchwarze/wifi-pineapple-panel) with fixes and improvements.
* Completely updated [packages repository](https://github.com/xchwarze/wifi-pineapple-community-packages) ([build](https://github.com/xchwarze/wifi-pineapple-community/tree/main/packages)).
* New [module repository](https://github.com/xchwarze/wifi-pineapple-community/tree/main/modules).
* And some new modules that are basic to use a device like this nowadays. New modules: [PMKIDAttack](https://github.com/xchwarze/wifi-pineapple-community/tree/main/modules/src/PMKIDAttack) and [Terminal](https://github.com/xchwarze/wifi-pineapple-community/tree/main/modules/src/Terminal)
* I also carefully checked every dependency that was installed on the device in order to have more free space on the main partition.

![Panel](assets/termidor-mipsel.png)

[Shuriken Hacks](https://www.youtube.com/@shurikenhacks) and [Shuriken Hacks - Build a $23 Wi-Fi Pineapple in 6 Minutes — EASIEST Method!](https://www.youtube.com/watch?app=desktop&v=udnxagkSzoA)
## Builds

You can find the complete steps to build this project in [this document](build.md). I have also added several important notes that will help you to try porting to other devices.
<br>

If you are interested in developing tools of this type, you may find my new development interesting [Frieren](https://github.com/xchwarze/frieren)
<br>


## Supported devices

There are 211 identified devices that can perfectly run the development. You can see the full [list here](devices.md).
<br>

Also I made a second repo for [downloads](https://gitlab.com/xchwarze/wifi-pineapple-cloner-builds) where you can find the firmwares already made for the most common devices of the Supported devices list.
<br>

**If your device is not in the list or you just want something more modern you can try my other project [Frieren](https://github.com/xchwarze/frieren)**
<br>

## What differences are there with other methods using by firmwares that I can download from the internet?

All the firmwares found on the internet have been created using the [securityaddicted method](https://www.securityaddicted.com/2016/11/17/weaponizing-gl-inet-gl-ar150/), which involves duplicating the entire original file system. However, this approach consumes excessive space and often leads to instability. As a result, I have developed a new and improved method.

I introduced this new method during my presentations about hardware porting at EkoParty 2020 and DragonJar 2021. You can access the materials from those [presentations here](https://github.com/indetectables-net/embedded).

In 2021, an [idiot named Samy Younsi](https://github.com/xchwarze/wifi-pineapple-cloner/issues/5), shamelessly plagiarized the method I had developed and presented at conferences. Months later, he adapted it to Python using the Wifi Pineapple Cloner v1 version and continued spreading it as his own creation.

Throughout 2022, I debugged the method and mastered its usage, enabling me to successfully port the pineapple to any hardware and achieve flawless functionality, identical to that of the original device.

Therefore, the most refined method I have devised not only significantly reduces the firmware's file size but also guarantees stability comparable to the original hardware.<br>
<br>


## Install steps

1. Install OpenWrt version 19.07.7 on your router.
<br>

2. Use SCP to upload the [firmware image](https://gitlab.com/xchwarze/wifi-pineapple-cloner-builds) in your device.
```bash
scp gl-ar750s-universal-sysupgrade.bin root@192.168.1.1:/tmp 
root@192.168.1.1's password: 
gl-ar750s-universal-sysupgrade.bin                                                                        100%   13MB   2.2MB/s   00:05 
```
<br>

3. Once the image is uploaded, execute sysupgrade command to update firmware. Wait few minutes until the device install the new firmware. 
```bash
ssh root@192.168.1.1
sysupgrade -n -F /tmp/gl-ar750s-universal-sysupgrade.bin
```
<br>

4. Enter to pineapple panel and enjoy! `http://172.16.42.1:1471/`

In the [download](https://gitlab.com/xchwarze/wifi-pineapple-cloner-builds) repo you can find some debugging tips if you have problems.
<br>

5. Once installed, the project has a tool that helps us to do several things.
For example you can use it to change the panel theme with this command:
```bash
wpc-tools theme_install
```


## Recomended setup

1. [GL-MT300N-V2 (Mango)](https://www.amazon.com/dp/B073TSK26W/ref=sspa_dk_detail_1?psc=1&pd_rd_i=B073TSK26W&pd_rd_w=YrL2k&content-id=amzn1.sym.8c2f9165-8e93-42a1-8313-73d3809141a2&pf_rd_p=8c2f9165-8e93-42a1-8313-73d3809141a2&pf_rd_r=ZVN4G4KHNY9CFT51XBPB&pd_rd_wg=58ay9&pd_rd_r=a45beb76-df84-4dd8-8432-42afafb3529f&s=electronics&sp_csd=d2lkZ2V0TmFtZT1zcF9kZXRhaWw) or [GL.iNet GL-MT300N-V2 (Mango)](https://store-us.gl-inet.com/products/usa-only-mango-gl-mt300n-v2?_pos=3&_sid=666f74d9c&_ss=r) or [GL-AR300M16 (shadow)](https://www.amazon.com/gp/product/B0777L5YN6/ref=ox_sc_act_title_4?smid=A364119SDJA4QG&th=1) or [GL.iNet GL-AR300M16](https://store-us.gl-inet.com/products/us-local-delivery-shadow-mini-smart-router-powerful-wireless-performance-travel-wifi-gl-ar300m16?_pos=1&_sid=8f55f079d&_ss=r)

2. USB 2.0 [Plugable 2.0 USB hub](https://www.amazon.com/Plugable-2-Port-Compact-Splitter-Windows/dp/B005HKIDF2/ref=sr_1_4?dib=eyJ2IjoiMSJ9.RodeNmig5UkuwttEJT2kpI0tZ4FZ1ue_EcmIwLuwdqdlbBBpjaLeHwBSDX4OSPvthrio-R9D3OE5bN2jSrNxTYo6OmbNWiwEk_Ckj7rHqiZxFoyWZpj_anwiPnVQB4pppqW77OAxmLmFf_h4-i5sC4zANJd_qz7PP-I6LsFGgAwjSnVNfhthYBAP08mYdEyRuaJgbDY5fBPGcXjgMkHIT3FqHkQG4vA40lynLvaO8sE.fdmFpsYKhKqbIoE9pNDQsL88hXJt7w9k-BWl-ZizmFw&dib_tag=se&hvadid=630952701965&hvdev=c&hvlocphy=9016238&hvnetw=g&hvqmt=e&hvrand=14553071782429434189&hvtargid=kwd-15510380&hydadcr=24661_13626712&keywords=2+port+usb+hub&qid=1736013838&sr=8-4) or [ANDTOBO 【2024 Upgraded】 USB 2.0 hub](https://www.amazon.com/Female-Splitter-Power-Extension-Adapter/dp/B07CKQSTCB/ref=sr_1_5?dib=eyJ2IjoiMSJ9.RodeNmig5UkuwttEJT2kpI0tZ4FZ1ue_EcmIwLuwdqdlbBBpjaLeHwBSDX4OSPvthrio-R9D3OE5bN2jSrNxTYo6OmbNWiwEk_Ckj7rHqiZxFoyWZpj_anwiPnVQB4pppqW77OAxmLmFf_h4-i5sC4zANJd_qz7PP-I6LsFGgAwjSnVNfhthYBAP08mYdEyRuaJgbDY5fBPGcXjgMkHIT3FqHkQG4vA40lynLvaO8sE.fdmFpsYKhKqbIoE9pNDQsL88hXJt7w9k-BWl-ZizmFw&dib_tag=se&hvadid=630952701965&hvdev=c&hvlocphy=9016238&hvnetw=g&hvqmt=e&hvrand=14553071782429434189&hvtargid=kwd-15510380&hydadcr=24661_13626712&keywords=2%2Bport%2Busb%2Bhub&qid=1736013838&sr=8-5&th=1) or [VIENON 3-Port USB hub](https://www.amazon.com/3-Port-Wireless-Extender-Splitter-MacBook/dp/B0C3TWLPTS/ref=sr_1_9?dib=eyJ2IjoiMSJ9.RodeNmig5UkuwttEJT2kpI0tZ4FZ1ue_EcmIwLuwdqdlbBBpjaLeHwBSDX4OSPvthrio-R9D3OE5bN2jSrNxTYo6OmbNWiwEk_Ckj7rHqiZxFoyWZpj_anwiPnVQB4pppqW77OAxmLmFf_h4-i5sC4zANJd_qz7PP-I6LsFGgAwjSnVNfhthYBAP08mYdEyRuaJgbDY5fBPGcXjgMkHIT3FqHkQG4vA40lynLvaO8sE.fdmFpsYKhKqbIoE9pNDQsL88hXJt7w9k-BWl-ZizmFw&dib_tag=se&hvadid=630952701965&hvdev=c&hvlocphy=9016238&hvnetw=g&hvqmt=e&hvrand=14553071782429434189&hvtargid=kwd-15510380&hydadcr=24661_13626712&keywords=2%2Bport%2Busb%2Bhub&qid=1736013838&sr=8-9&th=1)

3. Generic [RT5370 WIFI adapter](https://www.amazon.com/gp/product/B0DF85916V/ref=ox_sc_act_title_3?smid=A3DRTYKBW9O86F&psc=1) or [MT7612U WIFI adapter](https://www.amazon.com/Network-AWUS036ACM-Long-Range-Wide-Coverage-High-Sensitivity/dp/B08BJS8FXD/ref=sr_1_1?crid=59PF1GGJFK77&dib=eyJ2IjoiMSJ9.LdXwdEDXIXggONLR8kdXb_iIWxpQqRatNDVACNWMj2JlS3DNGlfVLOFtMyE2X26ukBtr5SMFRL075k2Wg2RxUVgxTEN1CuMpLDSWnCpjuObZQ4nTgYShNNscxvOhVs5uZcXVfu9vKRnTDCMWhvFSK989jX4UKCBidDgxkKUWtuffKCSDtVx3dNZXliqmohzx_9qr0QQP-mvLH8VcJlqPg6WiwhJ91Lol9Y189nemwv0.TXzXYAd913uD_OCzJIWLUYt02cD-48f-UIYe_K3-XEA&dib_tag=se&keywords=mt7612u&qid=1736012480&sprefix=mt7612u+wifi+adapter%2Caps%2C314&sr=8-1) **you're really going to need this on hardware that doesn't have two wifi adapters**

4. Please support Hak5 work and buy the new hardware!


## Patreon and Tips!

Those who want to help buy testing hardware or just give me a tip, you can do it by sending donations to my Binance account.
I also made a [Patreon](https://www.patreon.com/xchwarze) account where I share private builds and tests. Here you can find updates for the **Pineapple Nano** and builds to **improve stability** on 5g.

[![patreon](assets/patreon.png)](https://www.patreon.com/xchwarze)
![binance-qr](assets/binance-qr.png)
