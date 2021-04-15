Step to create shutdown switch

    Connect switch to GPIO3.

    Add config device tree overlays
    sudo nano /boot/config.txt

Insert this to the bottom
    dtoverlay=gpio-shutdown,gpio_pin=3,active_low=1,gpio_pull=up



     Create file 
     sudo nano /etc/udev/rules.d/99-gpio-power.rules


And insert this 
    ACTION!="REMOVE", SUBSYSTEM=="input", KERNEL=="event*", \
                            SUBSYSTEMS=="platform", DRIVERS=="gpio-keys", \
                            ATTRS{keys}=="116", TAG+="power-switch"

    And restart raspberry pi.


*** I2C must be deactivated if you use GPIO3 *** 




+  = Pin 2 (5v)
NO = Pin 5 (GPIO3)
C  = Pin 6 (GND)
-  = Pin 9 (GND)
