# CRON

'>' command writes to the cron.log file. It overwrites whatever was previously in the file.

'>>' appends output to the cron.log file. Does not overwrite previous entries.

### Crontab Commands

```crontab -e``` Edit or create a crontab file if it doesn't already exist.
```crontab -r``` Remove the crontab file.
```crontab -v``` Display the last time your crontab file was edited. (Only available on a few systems.)

### Crontab Parameters

minute hour day_of_month day_of_week command

+m - Minute - 0 to 59
+h - Hour - 0 to 23
+dom - Day of Month - 0 to 31
+mon - Month - 0 to 12
+dow - Day of Week - 0 to 7 (0 and 7 are both Sunday)

### Special Characters

We can use special characters in cron to allow users to specify time intervals in which the job should run. These special characters can be used in crontabs for declaring cronjobs.

Special Char: Asterick

The Asterisk is the wild card character that is used to specify for all the occurence of that parameter it is used for.

```bash
* * * * * /path/to/some/script
```

Special Char: Comma

The Comma is used when creating a list (i.e. when declaring 2 or more execution times of a command.

```bash
0,15,25 * * * * /path/to/some/script
```

Special Char: Hyphen

The Hyphen is used to specify the range of time in which the script can run.

```bash
0-59 0-23 * * * /path/to/some/script
```

Special Char: Forward Slash

The Slash is used to create specified intervals of time within a range.

````bash
* /20 * * * * /path/to/some/script
````

### Crontab Examples

Most crontabs can have multiple methods as they can be scheduled in many ways, like using wild cards or just defining a range.

##### Every minute of every day

````bash
# m h  dom  mon  dow  command
  * *   *    *    *   /path/to/some/script.sh
````

### Cron Scheduler

+[crontab.guru](https://crontab.guru/)
+[Cron Maker](http://www.cronmaker.com/)
+[Crontab Generator](https://crontab-generator.org/)
