launchpad-linux-driver
======================

## TI Lauchpad MSP430 kernel module fix

Getting a TI Launchpad MSP430's serial connection is a pain. This is what
worked for me under a recent kernel (3.12.8-300) under Fedora 20.

Simply run "make", and if it builds you should back up your cdc-acm.ko module
somewhere and replace it with the one you just built, then run "depmod -a" and
replug your device.

If it doesn't work you probably have the wrong kernel version. Check the
references below.

Run this command to find where your should replace the cdc-acm.ko file.

```echo /lib/modules/$(uname -r)/kernel/drivers/usb/class/```

My board is a rev 1.5 with a MSP430G2553. I did NOT cross the TXD/RXD jumpers,
they are in the original position.

### References

* https://github.com/capnm/LaunchPad Original source of this fix. If your
  kernel is older you should try this instead. Also contains udev rules
  which you should probably check out.


