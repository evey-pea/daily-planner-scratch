# Daily Planner Feature Set

## Overview

This file lists the desired features of the application.

### Main Features

The Daily Planner application main features are:

- Plan time spent on activities across the course of each day
- Activities (time periods) are listed like the appearance of a todo list
- Calculate the time periods of each activity if they are not supplied

### Expanded features

Additional features to have as part of the application are:

- Alerts issued for reminders for the following:
  - Breaks
  - Preset Interval (minor tasks/alarms independent of activities list)
  - Rationing intervals (based on last activity with count down timer before next occurence)

## Daily Activity List

The daily activity should resemble a list similar to the following:

```markdown
| Start | Activity                                         | Minutes |
| ----- | :----------------------------------------------- | ------: |
| 1000  | Daily Planning, Email, Slack                     |      15 |
| 1015  | Typing practice                                  |      25 |
| 1040  |                                                  |      50 |
| 1130  | _Break_                                          |      10 |
| 1140  |                                                  |      80 |
| 1300  | _Lunch_                                          |      30 |
| 1330  | Email, Slack                                     |      10 |
| 1340  |                                                  |     110 |
| 1530  | _Break_                                          |      10 |
| 1540  | Email, Slack                                     |      10 |
| 1550  |                                                  |     110 |
| 1740  | Daily Journal, Timesheet, Git Push, Housekeeping |      20 |
```

The activity list for each day should be able to be populated from combination of a preset list of activities and blank spaces

### Activity Item Data

Each activity should have the following data

- Activity type
  - _Default_ Blank template
  - _Optional_ Linked to an activity
    - Preset recurring activity (ie breaks and routine things)
    - Ongoing activities (ie projects)
- Title description of the activity
  - _Default_ Taken from linked activity title
  - _Optional_ User supplied
- Start time
  - _Default_ Calculated from previous activity start time plus duration
  - _Optional_ User suppplied
- Duration in minutes
  - _Default_ Calculated from activity start time to start of next activity
  - _Optional_ User supplied

### Activity User Workflow

1. Specify start and end times for activity list
2. Add recurring tasks (ie breaks and routine activities)
3. For blank activity sessions
   a. User nominates activity
   - Links activity or picks from activities list
     b. Duration can be set by user
4. For Existing activity sessions
   a. User can update:
   - start time
   - duration
   - title and/or linked activity
