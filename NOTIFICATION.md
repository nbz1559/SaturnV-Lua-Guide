# Notifications

Notifications are how you communicate to the user. I have not made a custom notification UI yet, i will in the future but for now im using GTA's notification feature.
If you dont want to write your notification out by hand, you can use my API below.

# void notification.show("Message")
To do this, all you have to do is replace Message with your text, then your done.
If you want to make your text a different colour, you could do something like
```notification.show("~r~Red~w~White")```
That will show a notification with the the text "Red" in red, and the text "White" in white. To use other colours, just use their first letters.

# void notification.log("Info", IncludeDate)
If IncludeDate is set to true, then the time and date will be displayed alongside your information.

This prints information to the log found in ```%appdata%\SaturnV\InfoLog.txt```
If you want to print out an error type information, use the following below.

# void notification.log_error("Info")
This prints information in the error style format to the log found in ```%appdata%\SaturnV\InfoLog.txt```
This one doesn't have a IncludeDate because ive set it like that.
