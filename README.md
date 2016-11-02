# Panthers_GameDay_Bot
To make this work, you need to know a little about using PRAW, Python(3.5 preferably you heathen), PHP, XAMPP, WGET, and TaskScheduler for windows.

I don't have the time to go over the exact hows right now, but here's the basic.


Use XAMPP to start an Apache server on your machine. In the /htdocs/ folder, stick the BasicTest.PHP file. 

Use TaskScheduler for Windows (if you have linux, you should be teaching me how to do this instead) to poll that webpage on your localhost every 5 minutes (create two tasks and schedule them each to do polls every five minutes, one starting at 00 and one starting at 03 to guarantee you have updated stats every 2.5 minutes).

Every 2.5 minutes, triggering WGET with the location of your BasicTest.PHP will cause the JSON request to happen, pull data from the NFL, and compile it into a file (look at the PHP code and figure out where it's saving).

Use TaskScheduler to run the GameDayBotV1.py file a few minutes before the game.

If you've filled in the info on Config_Bot.py (username, password, title, subreddit) the bot will do this:

GameDayBotV1.py launches
It imports all the registers (NAME, PASS, TITLE, SUBREDDIT) from Config_Bot.py and establishes a connection with reddit (identifying itself as the gameday bot), and posts a thread with the the initial phrase of "Happiness is Not A Place" (on future posts, it will post the contents of the text file of BasicTest.PHP's output.

Because I'm a shit programmer, I then create a function that opens that text file, posts the contents of it, jumps into a never-ending loop that sleeps 15 seconds, reposts, then loops again. Just CNTRL+C the python program when you're done to make it stop.


In the future, I'll properly look into OAUTH for Reddit and all that. But for now, frig off Lahey.



Note: If the bot loses internet connection at any time, you will no longer be able to post to the previous thread and it will begin to create a new thread.

This is because reddit only has "POST" in it's PRAW languague. Post is for creating a post (or comment). Editing only happens as long as the bot that initially posted is still running or you create a database to store the game thread ID's, do constant lookups, and edit that way. That's more complicated than I have the ability or time for, so if the bot loses connection, create a second thread or manually post the contents of thisfile.txt to the thread every few minutes.

