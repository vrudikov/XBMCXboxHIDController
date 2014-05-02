XBMC Xbox HID Controller
========================

Control XBMC using an original Xbox controller on OS X

Installation
------------

### Dependencies

Install the necessary dependencies

- Install [XCode][0] or have `xcodebuild` available in your `$PATH`
- Install the [Xbox HID controller][1] driver<sup>1</sup>

---

<sup>1</sup> If you are running Mountain Lion, Mavericks, or higher, you will
need to install the latest version of this driver found in [this
blog post][2] by using this direct link
[http://xhd.cvs.sourceforge.net/viewvc/xhd/xhd/Release/xhd_2_0_0.dmg?revision=1.3.](http://xhd.cvs.sourceforge.net/viewvc/xhd/xhd/Release/xhd_2_0_0.dmg?revision=1.3)

---

### Compile and Intsall

Install this program by running

    git clone git://github.com/bahamas10/XBMCXboxHIDController.git
    cd XBMCXboxHIDController
    make
    sudo make install

How To
------

After you have followed the above installation steps, you can call the program
directly by running

    $ XBMCXboxHIDController
    analog deadzone of 30%
    sending events to 127.0.0.1:9777
    starting, ctrl-c to exit
    ^C

All events generated by the controller will be forwarded to XBMC over `UDP://127.0.0.1:9777`
(the EventServer API) and will conform to `gamepad.xml` found in `keymaps/` of XBMC.

Note that events will only be forwarded if an app by the name of `XBMC` currently has
focus.  When `XBMC` becomes inactive, no events are sent over UDP.  This behavior
can be overridden by supplying the `-a` switch.

Add `-v` to log every controller connection/disconnection and each UDP packet sent

    $ XBMCXboxHIDController -v
    analog deadzone of 30%
    sending events to 127.0.0.1:9777
    starting, ctrl-c to exit
    controller detected
    {button: dpadup, map: XG, down: 1, }
    {button: dpadup, map: XG, down: 0, }
    {button: dpaddown, map: XG, down: 1, }
    {button: dpaddown, map: XG, down: 0, }
    {button: B, map: XG, down: 1, }
    {button: B, map: XG, down: 0, }
    {button: white, map: XG, down: 1, }
    {button: white, map: XG, down: 0, }
    {button: black, map: XG, down: 1, }
    {button: black, map: XG, down: 0, }
    {button: back, map: XG, down: 1, }
    {button: back, map: XG, down: 0, }
    {button: A, map: XG, down: 1, }
    {button: A, map: XG, down: 0, }
    {amount: 6656, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 7680, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 8448, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 9984, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 10752, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 12288, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 13056, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 14336, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 14592, down: 1, map: XG, button: rightanalogtrigger, }
    {amount: 15104, down: 1, map: XG, button: rightanalogtrigger, }
    ^C

Usage
-----

    $ XBMCXboxHIDController -h
    usage: XBMCXboxHIDController

    control XBMC using an original Xbox controller

    options
      -a              always send events, default is to only send events when XBMC has the foreground
      -d <deadzone>   deadzone percentage for analog sicks, defaults to 30
      -h              print this message and exit
      -H <host>       host on which to listen, defaults to 127.0.0.1
      -p <port>       port on which to listen, defaults to 9777
      -v              enable verbose logging

License
-------

MIT License

[0]: https://itunes.apple.com/us/app/xcode/id497799835
[1]: http://xhd.sourceforge.net/
[2]: http://macman860.wordpress.com/2013/05/03/xbox-driver-for-mac-os-x-lion/
