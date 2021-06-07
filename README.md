# micropython_BB-Q10-Keyboard
MicroPython drivers for the Blackberry Q10 keyboard with the arturo182/solder.party controller board

---

# Synopsys
```
from kb_q10 import KB_Q10
from machine import Pin, I2C
i2c = I2C(0, sda=Pin(0), scl=Pin(1))
kb = KB_Q10(interrupt_pin=Pin(2))
# input a few keys on the keyboard module
print(kb.input_buffer)
# prints a string of the keypresses to the console
print(kb.keypresses)
# prints the full list of inputs to the console, including whether the key was pressed, held down for a time, or released
kb.keypresses.clear()
# clears the keypress buffer
kb.fade_down()
# fades brightness to 0
kb.fade_up()
# fades brightness up to 255
kb.fade_to(127)
# fades brightness to 50%
kb.backlight=0
# shuts off the backlight immediately
kb.callback=None
# disables the default callback (you should set your own, but you have the option to simply not have a callback)
kb.reset()
# resets the keyboard's controller, clearing the FIFO, any interrupt/GPIO/etc configuration
from kb_q10 import InterruptReason
# ... press a key on the keyboard ...
kb.last_interrupt
print(InterruptReason[kb._last_int_reason])
# prints "Keypress"
print(kb.pending_keys)
# prints the number of events that have yet to be read from the keyboard. if you disabled the default interrupt handler
#  and did not set your own which reads keys from the keyboard via its FIFO register, this will be a non-zero value
kb.read_key()
print(kb.input_buffer)
# prints the input buffer, which if cleared and then read_key is executed directly, should contain exactly one keystroke
```

Better documentation will be forthcoming eventually.
