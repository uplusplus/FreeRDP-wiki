**This page is not completed**

Command line syntax has massively changed, which also affects plugins. This page needs updating. See [CommandLineInterface](https://github.com/FreeRDP/FreeRDP/wiki/CommandLineInterface)

# Plugins list
* audin - Audio Input Redirection Virtual Channel Extension
* cliprdr - Clipboard Virtual Channel Extension
* drdynvc - Dynamic Virtual Channel Extension
* rdpdr - Device Redirection Virtual Channel Extension
* rdpsnd - Audio Output Virtual Channel Extension
* tsmf - Video Redirection Virtual Channel Extension

# Plugins usage

All plugins can be used by adding parameter `--plugin <plugin name>` in command line. But some plugins have extra parameters (sub-plugins). A plugin may have one or more parameters followed by its extra parameters.

Note: Extra parameters are triggered with '--data' and must be trailed for each plugin with '--' to mark the end of extra parameters for a particular plugin.

E.g.: `xfreerdp --plugin rdpsnd --data alsa latency:50 -- --plugin drdynvc --data tsmf audin -- serveradress`

## cliprdr

* `--plugin cliprdr` - Synchronize client and server clipboard data. This is the old syntax and now defunct. Use /a:cliprdr

## rdpsnd

* `--plugin rdpsnd --data alsa --` - use ALSA system
* `--plugin rdpsnd --data pulse --` - use PulseAudio
* `--plugin rdpsnd --data latency:50 --` - use rdpsnd with a given latency in ms 

## rdpdr

**If you want any redirection to work with Windows Server 2012 you MUST use --plugin rdpsnd before you use any rdpdr options.**

* disk

`--plugin rdpdr --data disk:<Name>:<Path> --` - redirect system **\<Path\>** as disk with name **\<Name\>**

Note: With freerdp version 1.0.2 the parameter "disk" is going to be replaced by "drive" for compatibility reasons to MS RDP. 

* smartcard

`--plugin rdpdr --data smartcard:<name> --` - redirect smartcard with name **\<Name\>** 

* serial

`--plugin rdpdr --data serial:<serialport>:<device> --` - Redirect serial port (e.g. COMx) to the server

* parallel

`--plugin rdpdr --data parallel:<parallelport>:<device> --` - Redirect parallel port (e.g. LPTx) to the server

* printer

`--plugin rdpdr --data printer:<printername>:<driver> --` - Redirect one or more printers to the server
 
Previously, if  both  **\<printername\>**  and  **\<driver\>** are omitted, the printer sub-plugin will automatically redirect all CUPS printers using  the default PostScript driver "MS Publisher Imagesetter". This is currently defunct.

## tsmf

* `--plugin drdynvc --data tsmf --` - enable multimedia redirect (note: read more on the MMR site of this wiki)
* `--plugin drdynvc --data tsmf:decoder:gstreamer --` - use gstreamer as media decoder.
That tsmf can be used rdpsnd needs to be enabled (eg --plugin rdpsnd --data alsa --) as well.

## audin

* `--plugin drdynvc --data audin --` - enable audio-in redirect (microphone)

## rail (RemoteApp mode)

* `--app --plugin rail --data "<exe_or_file>:<working_dir>:<arguments>" --` - Start RDP in RemoteApp mode, to launch only one application in seamless mode