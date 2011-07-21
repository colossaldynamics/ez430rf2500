ez430rf2500 - Updated kernel extension
======================================

This is an updated kernel extension that is codeless and just makes sure that
no other kernel extensions load when plugging in an Ti Launchpad programmer
(ez430rf2500) this then allows a tool like [mspdebug][1] to communicate with
the device.


# Installation

1. Open the project in Xcode 4.1
2. Click the run button
3. Show in Finder the ez430rf2500.kext that was created (under products), and
   drag it to your desktop.
4. Open Terminal.app

        sudo su
        cd /System/Library/Extensions
        cp -R /User/<username>/Desktop/ez430rf2500.kext .
        chown -R root:wheel ez430rf2500.kext
        chmod -R 755 ez430rf2500.kext

5. Reboot your system

At this point you should now be able to use mspdebug with the rf2500 driver to
talk to the Ti Launchpad.

---

The work was inspired by [westf][2] on the [Ti e2e][3] community, he wrote the
first and original codeless kernel extension, however due to changes in Lion
the original version did not compile, mostly due to renamed existing kernel
extensions (com.apple.kernel.iokit is not com.apple.kpi.iokit). Instead of
having a project moved from Xcode 3 to Xcode 4 with its own issues, I created
the project from scratch.

[1]: http://mspdebug.sourceforge.net/
[2]: http://e2e.ti.com/support/microcontrollers/msp43016-bit_ultra-low_power_mcus/f/166/p/18554/212659.aspx#212659
[3]: http://e2e.ti.com/
