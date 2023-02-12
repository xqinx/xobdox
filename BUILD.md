## Customize and Build

* Check out xobdox's zmk branch: https://github.com/xqinx/zmk/tree/xobdox
* If you'd like to change any key mappings, modify the keymap file in
  `app/boards/shields/xobdox/xobdox.keymap` according to zmk's key code
  [definitions](https://zmk.dev/docs/codes)
* compile each side's firmware seperately
  you might need to setup your build environment following instructions
  [here](https://zmk.dev/docs/development/setup)
  ```shell
  cd zmk/app
  # compile for left side
  west build -p -b seeeduino_xiao_ble -- -DSHIELD=xobdox_left
  # copy artifacts out of build dir so it doesn't get overwritten by the next
  compilation for the right side
  cp build/zephyr/zmk.uf2 SOME_WHERE_YOU_CHOOSE/xobdox_left.uf2
  ```
  ```shell
  # compile for right side
  west build -p -b seeeduino_xiao_ble -- -DSHIELD=xobdox_right
  cp build/zephyr/zmk.uf2 SOME_WHERE_YOU_CHOOSE/xobdox_right.uf2
  ```

## Flash
* connect either side of the keyboard to your host machine using a USB-C cable
* double press the reset button on XIAO ble board. See
  [referece](https://wiki.seeedstudio.com/XIAO_BLE/)
* you should see a USB mass storage device show up after double pressing, that
  means the board now is in its bootloader and can be flashed over USB
* drag and drop the compiled firmware (xobdox_left.uf2 or xobdox_right.uf2
  depending on the side) to the mass storage device
* The board will flash itself and reset after it's done.
* Repeat this for the other side.


