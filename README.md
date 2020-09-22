Power BI Refresher
======
Script for automation of refreshing Power BI Desktop workbooks.
Edited on Python 3.8 with pywinauto, pyautogui.

Based on:
------
Original Script - https://github.com/dubravcik/pbixrefresher-python | 
Script - https://github.com/LevonPython/PbiRefresher | 
Solution - https://github.com/pywinauto/pywinauto/issues/943 | 

Added compatibility to PowerBI Version 2.84.981.0 (August 2020) on Windows 10 with English/Portuguese(Brazil) locales.

Installation
------
Install Windows SDK (https://developer.microsoft.com/en-us/windows/downloads/sdk-archive/) |

Install script using `pip`


```
pip install pbixrefresher
```

Usage
-----
Before runing the Script, run Inspect.exe (included in Windows SDK instalation folder)

```
pbixrefresher <WORKBOOK> [-workspace <WORKSPACE>] [--refresh-timeout <REFRESH_TIMEOUT>] [--no-publish]

where <WORKBOOK> is path to .pbix file
      --workspace <text> is name of online Power BI service work space to publish in (default My workspace)
      --refresh-timeout <number> is time in seconds to wait to refresh end (default 30000)
      --no-publish is switch to just refresh and save the workbook and skip publishing to online service (default False)
      --init-wait <number> is time to wait until Power BI Desktop starts (default 15)
```

Scheduling in Windows Task Scheduler
-----
Please keep in mind that this script uses GUI of Power BI Desktop and it needs that a user is logged in Windows session. You should also deactivate lock screen time. Ideally you should schedule the script on a computer where the GUI is not used to not interfere the scripting, for example dedicated Virtual Machine.

1. Open Task Scheduler
2. Click Create Basic Task
3. Fill a Name and click Next
4. Set a trigger and click Next
5. Pick Start a program as an action and click Next
6. in Program/script type absolute path to pbixrefresher.exe in your scripts folder in Python installation path (for example "C:\ProgramData\Anaconda3\Scripts\pbixrefresher.exe")

   in Arguments type file name of the workbook (for example "sample.pbix")
   
   in Start in type absolute path workbook (for example "C:\workbooks\")
7. Confirm and Finish

Running on a VM
-----

If running on a VM you can use the closesession.bat, just edit the username with yours.
the scrip closes the session but maintein the gui active so the scrip can work.

See how it works
-----
[![pbixrefresher](http://img.youtube.com/vi/8HSK_-1ULro/0.jpg)](https://www.youtube.com/watch?v=8HSK_-1ULro "pbixrefresher")
