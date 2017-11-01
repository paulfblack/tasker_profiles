# Silent When Busy  
## Overview    
This is a simple profile that turns your phone to do not disturb mode during events on your calendar that are marked as busy. 
This profile is useful if you differentiate between "busy" and "not busy" events on your calendar and will prevent you from being 
"that guy" who's phone goes off during a meeting. For this implementation I set it to full silent mode, meaning not even priority contacts 
will be able to get through. This is because I have set up another profile [emergeny call](https://github.com/paulfblack/tasker_profiles/tree/master/volume_controls/emergency_call) 
which allows for "important" contacts to override current volume settings if they call three times in a row within the same hour.  
  
The idea behind not letting priority contacts through is that your busy times are not always predictable to priority contacts. Perhaps you 
have family memebers or roommates saved as priority, but you don't want your phone to ring in a business meeting just because your mother 
called to see how you were doing.  
  
This profile will take any calendar event and check to see if you are "busy". If you are "busy" do not disturbe mode is turned on. 
When the event ends do not disturb is turned off if it was not previously on, thus restoring volume settings to their previous state.  
  
## Requirements:  
  
- This implementation requires that you use google calendar (might work as is with other calendars, but not tested).  
- You must differntiate between busy and not busy events for this profile to be useful.  
  
## Downloads and Tasks:  
  
This profile can be downloaded in it's entirety from [silent_when_busy.prf.xml](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/silent_when_busy/silent_when_busy.prj.xml) or as individual tasks and profiles.  
  
### [Profiles:](https://github.com/paulfblack/tasker_profiles/tree/master/volume_controls/silent_when_busy/profiles)  
- [Silent Mode - Calendar Busy](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/silent_when_busy/profiles/silent_mode_calendar_busy.prf.xml)  
  
### [Tasks:](https://github.com/paulfblack/tasker_profiles/tree/master/volume_controls/silent_when_busy/tasks)  
- [Volume Off](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/silent_when_busy/tasks/volume_off.tsk.xml)  
- [Restore Volume](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/silent_when_busy/tasks/restore_volume.tsk.xml)  
  
## Suggested edits:  
- Replace Do Not Disturb Mode with individual volume control to keep vibrate on.  
> - You can store previous volume settings in custom variables to restore upon exit.  
- Use specific calendars instead of "busy" (i.e. any event on "work" calendar).
- Allow priority calls to come through.
- Use other event features (e.g. name, location, description) to control this profile.  
  
## Custom Variables  
  
**DoNotDistrub** - This variable stores the value of **%SILENT** when the task is triggered. This allows Do Not Disturb to be 
turned off if **%SILENT** was Off at the start of the task. **%SILENT** is On if Do Not Disturb is set to on and off otherwise.  
  
> **note:** it is important that this variable has at least one capital letter to make it a global variable as it is set in the task volume off 
and checked in the separate task restore volume.  
