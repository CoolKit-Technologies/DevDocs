<!--
 * @Author: Carl
 * @Date: 2021-01-29 18:11:12
 * @LastEditors: Carl
 * @LastEditTime: 2021-02-03 17:34:03
-->

# Protocol for controlling eWeLink Camera app via third-party Bluetooth devices

## 1. Product introduction

eWeLink Camera app is a mobile application that turns an Android smartphone into a webcam.

You can use eWeLink Camera app as a baby monitor, pet camera, and security camera. Taking advantage of a retired smartphone, you can save the cost of a new security camera.  

<div align=center>
<img src="./1.jpg" width="500" height="auto" />
</div>

## 2.Connect with your own Bluetooth devices

Currently, eWeLink Camera app can connect with eWeLink gimbal(Bluetooth) for users to pan and tilt the gimbal in eWeLink app remotely so as to change the angle of the camera and have better view.

For the convenience of makers, the Bluetooth protocol is open for review as follows.

Users can connect the phone camera with certain types of Bluetooth devices in eWeLink app and control the Bluetooth devices via the Bluetooth commands offered by CoolKit or customized Bluetooth commands.

### 2.1 Move the gimbal

You can: specify the direction and angle of the movement or keep moving the gimbal.

| 2 Bytes | 2 Bytes     | 1 Bytes   | 2 Bytes | 1 Bytes  |      1 Bytes |
| ------- | ----------- | --------- | ------- | -------- | ------------ |
| cmd_id  | data_length | direction | degrees | velocity | sum          |
| 0x0001  | 0x0004      | 0x01      | 0x000F  | 0x1E     | 0x15         |

Parameters：

- cmd_id：0x0001（Move the gimbal）；
- data_length：Data length；
- direction：0x01 Leftward, 0x02 Rightward, 0x03 Upward, 0x04 Downward, 0x00 Stop moving；
- degrees：Designate the angle for the movement（Range 0x0001-0x0167）. To keep the movement or stop it, pass 0x0000；
- velocity：Angular velocity(How many angles the gimbal rotates per second rad/s). This value is only effective when the gimbal keeps rotating. The suggested range is 1~60.
- sum：The checksum of all commands, which is the sum of the values of all the fields above(from cmd_id to velocity). 

Note: In the process of executing a command, if a new command is received, the gimbal will rotate according to the new command.

**Other commands to be completed**