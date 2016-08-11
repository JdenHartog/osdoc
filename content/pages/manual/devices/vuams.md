title: Ambulatory Monitoring System (VU-AMS)

The VU University Ambulatory Monitoring System (VU-AMS) is a device that can be used to measure a variety of factors related to heart rate, respiration, and body movement. The developers made an OpenSesame [plugin](https://github.com/JdenHartog/vu_ams).

- <http://www.vu-ams.nl/>

%--
figure:
 id: FigVuamsDevice
 source: VU-AMS.png
 caption: |
  The VU-AMS device.
--%

[TOC]

## Using the `vu-ams` plugin

Parallel_port_trigger is a third-party plugin.
{: .page-notification}

Markers can be sent with the `vu-ams` plugin which currently works under **Windows only**.

The plugin has three input boxes:

- The *Device name* can be autodetect or can be specified manually.
- The *Send marker* value ranges between 0-65535 and specifies the marker number to send.
- The *Use number from title* checkbox allows you to use a number from the item title to send.
- The *Use without VU-AMS device* checkbox allows you to run your experiment without a VU-AMS connected and recording.

You can download the plugin from here:

- <https://github.com/JdenHartog/vu_ams>

%--
figure:
 id: FigScreenshot
 source: plugin-screenshot.png
 caption: |
  A screenshot of the `vu-ams` plugin.
--%

## Setting the device name

By default, the plugin tries to autodetect the VU-AMS. If this works, you don't have to change it. If your experiment stops, OpenSesame can't automatically detect the port and you must enter the device name manually. Under Windows, the device is called something like

	COM3

Note that entering a device name manually makes your experiment start a bit faster because than the plugin doesn't have to sequentially  try all ports.

## Requirements

A VU-AMS device see:

- <http://www.vu-ams.nl/>

## Using the vu-ams from Python inline code

# class __AMS__

If you insert the vu-ams plugin at the start of your experiment, an
instance of `AMS` automatically becomes part of the `var`
object and can be accessed within an inline_script item as `var.AMS

__Function list:__


- [function __srbox\.\_\_init\_\___\(experiment, dev=None\)](#function-__srbox__init____experiment-devnone)
- [function __srbox\.close__\(\)](#function-__srboxclose__)
- [function __srbox\.get\_button\_press__\(allowed\_buttons=None, timeout=None, require\_state\_change=False\)](#function-__srboxget_button_press__allowed_buttonsnone-timeoutnone-require_state_changefalse)
- [function __srbox\.send__\(ch\)](#function-__srboxsend__ch)
- [function __srbox\.start__\(\)](#function-__srboxstart__)
- [function __srbox\.stop__\(\)](#function-__srboxstop__)



__Example:__

~~~ .python
t0 = clock.time()
srbox.start()
button, t1 = srbox.get_button_press(allowed_buttons=[1,2],
        require_state_change=True)
if button == 1:
        response_time = t1 - t0
        print('Button 1 was pressed in %d ms!' % response_time)
srbox.stop()
~~~

## [function __srbox\.\_\_init\_\___\(experiment, dev=None\)](#function-__srbox__init____experiment-devnone) {#function-__srbox__init____experiment-devnone}

Constructor. An `srbox` object is created automatically by the `srbox` plug-in, and you do not generally need to call the constructor yourself.

__Arguments:__

- `experiment` -- An Opensesame experiment.
	- Type: experiment

__Keywords:__

- `dev` -- No description
	- Default: None

</div>

[srbox.__init__]: #srbox-__init__
[__init__]: #srbox-__init__

<div class="FunctionDoc YAMLDoc" id="srbox-close" markdown="1">

## [function __srbox\.close__\(\)](#function-__srboxclose__) {#function-__srboxclose__}

Closes the connection to the srbox. This is done automatically by the `srbox` plugin when the experiment finishes.

</div>

[srbox.close]: #srbox-close
[close]: #srbox-close

<div class="FunctionDoc YAMLDoc" id="srbox-get_button_press" markdown="1">

## [function __srbox\.get\_button\_press__\(allowed\_buttons=None, timeout=None, require\_state\_change=False\)](#function-__srboxget_button_press__allowed_buttonsnone-timeoutnone-require_state_changefalse) {#function-__srboxget_button_press__allowed_buttonsnone-timeoutnone-require_state_changefalse}

Collects a button press from the SR box.

__Keywords:__

- `allowed_buttons` -- A list of buttons that are accepted or `None` to accept all buttons. Valid buttons are integers 1 through 8.
	- Type: list, NoneType
	- Default: None
- `timeout` -- A timeout value in milliseconds or `None` for no timeout.
	- Type: int, float, NoneType
	- Default: None
- `require_state_change` -- Indicates whether already pressed button should be accepted (False), or whether only a state change from unpressed to pressed is accepted (True).
	- Default: False

__Returns:__

A button_list, timestamp tuple. button_list is None if no button was pressed (i.e. a timeout occurred).

- Type: tuple

</div>

[srbox.get_button_press]: #srbox-get_button_press
[get_button_press]: #srbox-get_button_press

<div class="FunctionDoc YAMLDoc" id="srbox-send" markdown="1">

## [function __srbox\.send__\(ch\)](#function-__srboxsend__ch) {#function-__srboxsend__ch}

Sends a single character to the SR Box. Send '`' to turn off all lights, 'a' for light 1 on, 'b' for light 2 on,'c' for lights 1 and 2 on etc.

__Arguments:__

- `ch` -- The character to send.
	- Type: str

</div>

[srbox.send]: #srbox-send
[send]: #srbox-send

<div class="FunctionDoc YAMLDoc" id="srbox-start" markdown="1">

## [function __srbox\.start__\(\)](#function-__srboxstart__) {#function-__srboxstart__}

Turns on sending mode, so that the SR Box starts to send output. The SR Box must be in sending mode when you call [srbox.get_button_press].

</div>

[srbox.start]: #srbox-start
[start]: #srbox-start

<div class="FunctionDoc YAMLDoc" id="srbox-stop" markdown="1">

## [function __srbox\.stop__\(\)](#function-__srboxstop__) {#function-__srboxstop__}

Turns off sending mode, so that the SR Box stops giving output.

</div>

[srbox.stop]: #srbox-stop
[stop]: #srbox-stop

</div>

[srbox]: #srbox


[function __srbox\.\_\_init\_\___\(experiment, dev=None\)]: #function-__srbox__init____experiment-devnone
[function __srbox\.close__\(\)]: #function-__srboxclose__
[function __srbox\.get\_button\_press__\(allowed\_buttons=None, timeout=None, require\_state\_change=False\)]: #function-__srboxget_button_press__allowed_buttonsnone-timeoutnone-require_state_changefalse
[function __srbox\.send__\(ch\)]: #function-__srboxsend__ch
[function __srbox\.start__\(\)]: #function-__srboxstart__
[function __srbox\.stop__\(\)]: #function-__srboxstop__
















## Using `dportio.dll` in a Python inline Script (Windows only)

Instead of using the `parallel_port_trigger` plugin, it is also possible to send triggers with `dlportio.dll` through a Python inline script. This approach is Windows only. To do so, first add an INLINE_SCRIPT to the start of the experiment with the following code in the prepare phase:

~~~ .python
try:
	from ctypes import windll
	global io
	io = windll.dlportio # requires dlportio.dll !!!
except:
	print 'The parallel port couldn\'t be opened'
~~~

This will load `dlportio.dll` as a global object called `io`. Please note that failure will not crash the experiment, so make sure to check the debug window for error messages!

Now use the following code in an INLINE_SCRIPT anywhere in the experiment to send a trigger:

~~~ .python
global io
trigger = 1
port = 0x378
try:
	io.DlPortWritePortUchar(port, trigger)
except:
	print 'Failed to send trigger!'
~~~

Note that this sends trigger 1 to port 0x378 (=888). Change these values according to your set-up.


## Recommendations

- ???

## Troubleshooting

Make sure to close the VU-DAMS suite *device configuration window* as the VU-AMS device can 'talk' to one application at a time.

Please don't hesitate to post questions on the forum, or to let us know of your experiences (good or bad).

