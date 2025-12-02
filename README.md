# Aquarium-Controller---ESPHome-Home-Assistant
Aquarium controller programmed on ESPHome and used within Home Assistant that includes various sensors and a controlled relay.

## What is this?
This is an aquarium controller with built in capabilities for several sensors and relays. You can set a schedule for activating the relay on selected days and hours being able for example to control a valve for water changes.

### Let me know what this code includes
Well, on this repository you will find the needed files for setting this up on both ESPHome and Home Assistant. Some extra tweaking will be needed on the Home Assistant side to make this fully work, but the results really worth it.
The files are split into two directories, one for each platform.

## ESPHome
1. You will need to paste both the "irrigation.h" and "secrets.yaml" files directly to your ESPHome config directory. Please note that on the "secrets.yaml" file you will need to write your own information.
2. Then configure your new ESP32 board (if you are here you know how to do it) and once you have to write the code for this board you can just copy the code from the file "aquarium-controller-esp32.yaml".
3. Install the code into your board and you're good to go.

## Home Assistant
1. First make sure that your new board pops up on your Home Assistant devices. Once again, if you are reading this you know how it works.
2. Once you can see your sensors and switch or switches is time to copy the code from the "configuration.yaml" to yours.
3. At this point you won't see any major changes on what you see on your ESPHome device in Home Assistant.
4. In order for this to work you will need to set some helpers on Home Assistant matching this:
   a. Helper type: input_select
   * Name: irrigation_zone1_times
   * Options: here you will enter time values (hours) that you will likely select for the water change to start (activate the switch/relay).
  
   b. Helper type: input_select
   * Name: irrigation_zone1_days
   * Options: here you will enter the days of the week. You can enter one day per option or group them. For example, I had set them like this:
     - Option 1: Dom,Lun,Mar,Mie,Jue,Vie,Sab (for daily changes).
     - Option 2: Dom,Lun,Mie,Vie (for changing water on those days).
     - Option 3: Lum,Mie,Vie (for changing water on those days).
    
   c. Helper type: input_number
   * Name: irrigation_zone1_duration
   * Min value: 0
   * Max value: 120

Once you have set this up you will be able to make some nice dashboard for the controller. You can still configure some more helpers in order to modify the way you show the sensors data.

Hope you like this project!
