# Emergency Call  
## Overview:    
This profile allows for the automatic override of current volume settings for emergency purposes from contacts labelled "important".  
  
While phones allow for calls to come through on full volume from specified contacts when silent mode is active,
sometimes you don't want this to occur should the call not be urgent. This profile allows specified contacts to
override current volume settings if they call three consecutive times within the same hour. This implementation uses
a custom contacts label "important" from google's contact app. The profile stores your previous volume settings in
global variables and then reimplements them after the phone has been picked up and the call has ended. The number of 
attempted calls by an important contact only increases if the previous important caller and the current important caller
are the same and resets itself every hour.  

**Note:** Currently, if multiple important contacts try and call you volume profiles will only change when one of those contacts 
calls three times in a row, without another important contact calling in between. Calls from "non-important" contacts will not effect
volume profiles nor will they interrupt the counter for successive calls.  
  
The use cases this profile was designed for include:  
- Emergency situations where phone volume is low without allowing for mis-fires when important contacts call for non-emergencies.
- Silent mode is not active, but current phone volume is low.  
- Roommates/neighbors who have locked themselves out. Most calls from these contacts when the phone is on silent would not qualify as urgent, 
but this gives these contacts the ability to reach you during silent hours _only_ if it is necessary.
  
## Requirements:  
  
This implementation uses google's [contacts app](https://play.google.com/store/apps/details?id=com.google.android.contacts) and a custom
contact label "important". This is separate from I.C.E. contacts to allow for non-I.C.E. contacts access to the volume override (e.g. roommates
who might have locked themselves out). You can edit the used app and label in the profiles for Emergency Calls and Emergency Mode.


## Downloads and Tasks:  
  
This profile can be downloaded in it's entirety from [emergency_call.prf.xml](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/emergency_call/emergency_calls.prj.xml) or as individual tasks and profiles.  
  
### [Profiles:](https://github.com/paulfblack/tasker_profiles/tree/master/volume_controls/emergency_call/profiles)  
- [clear_prev_caller](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/emergency_call/profiles/clear_prev_caller.prf.xml)  
- [emergency_calls](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/emergency_call/profiles/emergency_calls.prf.xml)  
- [emergency_mode](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/emergency_call/profiles/emergency_mode.prf.xml)  
  
### [Tasks:](https://github.com/paulfblack/tasker_profiles/tree/master/volume_controls/emergency_call/tasks)  
- [important_call](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/emergency_call/tasks/important_call.tsk.xml)  
- [clear_prev_caller](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/emergency_call/tasks/clear_prev_caller.tsk.xml)  
- [emergency_mode_exit](https://github.com/paulfblack/tasker_profiles/blob/master/volume_controls/emergency_call/tasks/emergency_mode_exit.tsk.xml)  
  
## Suggested edits:  
- Only activate emergency call and clear prev caller when:  
> - Silent mode is active.  
> - Calendar is marked as busy.  
> - During specific hours (work day/sleep hours).
> - At a location other than home.
- Allow any 3 important callers to override volume settings (i.e. regardless of consecutive calls from one contact).
- Adjust previous caller variable reset rate.
