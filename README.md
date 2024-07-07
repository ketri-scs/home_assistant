# home_assistant
home assistant, ha

# zigbee dongle
## sonoff ZBDongle-E 
- ti 칩 아님
- 평판 좋지 않아 사용하지 않기로 함
## sonoff zigbee 3.0 usb dongle plus
- zigbee : cc2652p <- ti
- usb : cc2102n
### coordinator firmware
#### router firmware
- CC1352P2_CC2652P_launchpad_router_20221102.hex
#### flash firmware 
- ti flash programmer 2 -> Error -> 'Unknown record type: 3' -> firmware 개발자는 firmware 문제 없다고 하고 이 flash programmer 2에 버그가 있다고 함.
- cc2538-bsl.py -> ERROR -> int() can't convert non-string with explicit base
- zigbee-3.0-usb-dongle-plus-uartLog : for flash programmer 2 to enter flash mode
- ZigbeeStar GW Multi tool - 2021 - 0.41 -> flash ok : scs
- ![image](https://github.com/ketri-scs/home_assistant/assets/74283411/21dd441d-c372-42d5-8625-ce318a114494)

## tuya led 
- Zigbee Model: TS0505B
- Zigbee Manufacturer: _TZ3210_mja6r5ix
- Description: Zigbee 3.0 18W led light bulb E27 RGBCW
- Firmware version: z.1.0
- Model: TS0505B_2_1
### topic
#### subscribe
- zigbee2mqtt/test_led
  {"brightness":76,"color":{"h":2.1079772760419413,"hue":2.1079772760419413,"s":94.3829089764056,"saturation":94.3829089764056},"color_mode":"hs","color_temp":296,"do_not_disturb":false,"linkquality":135,"state":"OFF"}
#### publish
- zigbee2mqtt/test_led/set
{
  "state": "ON",
  "color": {
    "r": 255,
    "g": 0,
    "b": 0
  },
  "brightness": 90
}

### Scene Error
- tuya led 자체 scene 기능 버그
- settings -> automations & scenes -> script : service call에서 'MQTT: Publish'로 해결

### Router Error
- router 기능 스펙상 된다고 하나, 실제로는 안됨
