# Raspberry Pi 4B 常見配置與使用情境

## 關閉主板上的 LED

編輯 `/boot/config.txt` 檔案內容

```txt
# Turn off ethernet led
dtparam=eth_led0=4
dtparam=eth_led1=4

# Turn off act led
# dtoverlay=act-led,activelow=on
dtparam=act_led_trigger=none

# Turn off pwr led
# dtparam=pwr_led_trigger=none
# default
dtparam=pwr_led_trigger=default-on
dtparam=pwr_led_activelow=off
```
