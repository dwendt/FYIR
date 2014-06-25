# FYouI'mRoot

This is a Windows 7 driver(hopefully x86 and x86_64) that allows an administrator to endulge in the things they should rightfully be able to do on their own computer. Drivers that serve no purpose other than to prevent reverse engineering/development and make life difficult are increasingly common, as can be seen in PunkBuster, Ahnlabs HackShield(EagleNT.sys, Eagle64.sys), Tencent's TenProtect(TenSafe.sys), etc. Fuck that shit, this is my OS.

It will never be necessary to disable patchguard. To run this driver, you will need to self-sign it, todo: instructions will be provided.

Things this should be able to do:

* Dump/log files being written to that match a given name
* Prevent `ObRegisterCallback`s intended to deny process handle requests, by either:
	* Providing an API to request a handle via the driver
	* Walking the callback list kernel structure and removing those belonging to memory regions of some given driver
* Hide given process names from the process list. Really.

* Hide existance of a given module name from being seen in the PEB of any processes?
* Hide given file names on disk? -- might need a kernel patch :(
	* Alternatively, replace the original file path field of the `KPROCESS` structure for a given process name with something funny
* Dump a given running driver to disk?