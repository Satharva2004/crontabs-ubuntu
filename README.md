# crontabs-ubuntu

Perfect! I can see your project directory and your script: sprout_april.js. Let’s set up a cron job to run it every day. I’ll give you copy-paste commands for your current setup.

1️⃣ Find Node.js path

Run:

which node


Let’s assume it returns /usr/bin/node. If it’s different, use that path in the next steps.

2️⃣ Create a shell script to run your Node script

Run:

nano ~/Automation-excel-daily/run-sprout.sh


Paste the following:

#!/bin/bash
cd ~/Automation-excel-daily
/usr/bin/node sprout_april.js >> ~/Automation-excel-daily/cron-sprout.log 2>&1


Save and exit (Ctrl+O, Enter, Ctrl+X).

Make it executable:

chmod +x ~/Automation-excel-daily/run-sprout.sh

3️⃣ Add the cron job

Edit your crontab:

crontab -e


Add this line at the end (to run every day at 2:30 AM):

30 2 * * * ~/Automation-excel-daily/run-sprout.sh


Save and exit.

4️⃣ Verify cron job
crontab -l


You should see your new cron job listed.

5️⃣ Check logs after first run

After it runs at 2:30 AM (or you can temporarily change the time to a few minutes ahead to test):

cat ~/Automation-excel-daily/cron-sprout.log


This will show output and errors from your Node script.
