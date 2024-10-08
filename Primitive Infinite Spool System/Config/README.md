# Config Info

## Variable Store

The [gcode_macro _FILAMENT_VARS] macro is for storing variables that different macros can check/update. I plan on shifting more stuff into here and out of specific macros.

## Hardware

The hardware section is for filling out your pins and junk for *your* specific hardware. The ones in the included .cfg is what my printer is running, yours will be different.

## Your print_start macro

It's worth adding a couple of things to your print_start macro to allow the infinite spool system to run smoothly.

Near the top of my print_start macro I like to have a `SET_GCODE_VARIABLE MACRO=_FILAMENT_VARS VARIABLE=infinitespool VALUE=0` so the infintite spool system is
disabled *by default*, then I have a `SELECT_ACTIVE_SPOOL`, a `LOAD_FILAMENT`, and a `HARD_CHECK_FILAMENT_LOADED` to make sure a spool is active and the filament is
at the extruder.
The HARD_CHECK will cancel the print if filament isn't detected by the post_extruder sensor.

![image](https://github.com/user-attachments/assets/41eb758c-2239-40f6-9482-afed015a1207)




Then, as I usually want infinite spool when printing ABS I have this further down (in my "if filament is ABS" section):
```
 {% if params.FILAMENT_TYPE == 'ABS' %}
    RESPOND MSG="ABS Detected"
    {% if printer['filament_switch_sensor left_pre_stepper'].filament_detected and printer['filament_switch_sensor right_pre_stepper'].filament_detected %}
      INFINITE_SPOOL_ENABLE
    {% endif %}
  {% endif %}
```
which will enable infinite spool *if* the material is ABS and *if* it detects filament loaded in both sides.

You can always enable infinite spool during a print by running `TOGGLE_INFINITE_SPOOL_MODE` macro (and making sure that filament is loaded into both sides and triggering the pre-stepper filament sensors).


# Macros

The macros section is where all the magic happens. A lot of the macros there don't need to be touched as long as you are using the same number/type of sensors as outlined on the [main page](.).

## Activation

The `ACTIVATE_LEFT_SPOOL` and `ACTIVATE_RIGHT_SPOOL` will enable the left/right side of the system by un-syncing the opposite side and then syncing the activated side to the extruder and belay.

The `SELECT_ACTIVE_SPOOL` will automatically detect which side is active based on which side has the post_stepper filament sensor triggered (as long as *only* one side is triggered)

There is a delayed_gcode `INITIAL_ACTIVE_SPOOL` which will select the active spool on boot if the system is in the proper configuration.

`HARD_CHECK_FILAMENT_LOADED` is something I put at the top of my START_PRINT macro so it doesn't try to start printing with no spool activated (it will e-stop error if there is no current active spool)

## Removing Filament

The `REMOVE_FILAMENT` is the macro that is called whenever you want to remove the filament out the "top" of the system. It will only remove the currently active side.

The macro will do an initial slow pull to clear the extruder, then a longer fast pull to clear *most* of the bowden, then will do the final small steps checking if the sensor is triggered.
This is done with a loop which calls a seperate macro `_REMOVING_FILAMENT` each time the loop runs. This is needed because a macro will only check things (like filament sensors) *once* when the macro is first called. If you ask it to check a sensor again after an action it will just give you the initial state, not the current state.
So to work around that we are calling a *second* macro each iteration of the loop, and this `_REMOVING_FILAMENT_ macro will check the sensor each time and do something accordingly.

`_REMOVING_FILAMENT` will retract 10mm of filament each time it is called, but only if the post_stepper sensor for the active side is still triggered. Once the sensor is no longer triggered (because hte filament has been pulled past that point) it will stop retracting.

## Loading Filament

Loading filament acts similarly as removing filament, with one main `LOAD_FILAMENT` macro that will call a secondary `_LOADING_MACRO` on each iteration of a loop. It will do an initial fast push if there is 

If neither post_stepper sensors are triggered then the system assumes the filament path is empty and so will do an initial slow push to clear the filament sensors/Y splitter/encoder_sensor/belay and then will do a fast push to take it close to the extruder.
It will then do small hops until it has reached the post_extruder sensor.

## Infinite Spool Loading

I currently have `INFSPOOL_LOAD_FILAMENT` as a seperate macro as it is newer. I previously didn't have a pre-extruder sensor but after adding one I changed how infinite spool worked. 

Previously it would pull filament back out of the system and load in the other side, but I found sometimes the filament getting pulled would catch and jam if there was a tight bend/kink on the end of the filament (where it hooks into the spool).

The new method uses a pre-extruder sensor to trigger filament runout and instead of pulling the old filament out it just loads new filament in behind then extrudes the last 100mm of filament that is still in the extruder.

I might combine the INFSPOOL_LOAD_FILAMENT and LOAD_FILAMENT macros at some point.

## Toolchanging

These are testing T0/T1 macros that could theoretically used as a simple two-colour multi-material system. I haven't invested too much time into this as it needs a filament buffer to stop tangles and I haven't designed that yet.
