# Notion-GoogleTasks
This project allows you to sync a notion database with a calendar view with google tasks.

When called in a cron, for example,it first syncs Google task with notion then syncs notion with google tasks, searching for a property called "Status" and sees if it equals done. Everytime I do finish a task I change its status to done.
You can change the code to change the property name of course. It searches them on the Google task list and deletes them as they are, you guess it, done. Then, it reads the database and checks one per one if it is inside the  Google task list yet,and if it is not adds it!

Need to have a ```client_id.json``` get from the Google Calendar API, more info here: 
https://developers.google.com/calendar/quickstart/python

Also a ```settings.json``` file with this structure:
```
{
	"token":"xxxxxxxxx", # token_v2, it can be get from the cookies
	"url":"XXXXXXXXX",  #calendar view url, in the calendar view right clic -> copy view url
	"property":"deadline" #name of the property that holds a Date. In my case deadline, pretty straightforward
}
```
To get the tokenV2 I do explain it on my other notion repo here https://github.com/elblogbruno/NotionAI-MyMind.

This project was inspired why https://github.com/evertheylen/notion-export-ics and https://github.com/elblogbruno/Notion-GoogleCalendar-Sync that the idea to get it done is simpler, but this one I find it nicer and faster. 

## TODO
Google Task to notion sync. by the moment there is only notion to google task, not viceversa.


## FAQS

```
Traceback (most recent call last):
File ".../notion/notion-export-ics/webapp.py", line 38, in make_ics
cal = get_ical(client, calendar_url, title_format)
File ".../notion/notion-export-ics/notion_ics.py", line 27, in get_ical
calendar_query = calendar_view.build_query()
File ".../notion/collection.py", line 249, in build_query
"query"
KeyError: 'query'
```

If you get this error see this:

https://github.com/evertheylen/notion-export-ics/issues/5

