# Daily Planner Data Structure

## Purpose

The purpose of this document is to out line the data structure that is to form the basis that feeds into the ocmponents that are used in the front end application that are expected from the backend application.

## Todo List

Data structures needed to be defined in this document

- [x] Activity Item Definintion
- [x] Typescript Models
  - [x] Activity Interface
- [x] JSON examples
  - [x] Activity Item
  - [x] Daily Activity List
    - Start/End/Date
    - Array of activity Items
  - [x] Recurring Activity / Ongoing Planned Task List
- [ ] Angular Models
  - [ ] Activity Item Data
  - [ ] Activity List
  - [ ] Task List
  - [ ] Recurring Task List
  - [ ] Daily Activity
    - [ ] Date
    - [ ] Start and End time

## Activity Item Definition

Defined in the [Feature Set](/Feature-Set.md) document as the following:

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

## Models

The typescript type interface models are to be used as expected _Response_ models from the API

### Activity Item Typing

```typescript
interface ActivityType = {
  id: number,
  title: string
  description: string,
  daily: boolean,
  active: boolean
}

interface ActivityInterface = {
  id: number,
  activityType: ActivityType,
  date: string,
  startTime: string,
  duration: number,
}

```

### Activity Item

```json
{
  "id": 1,
  "activityType": {
    "id": 1,
    "title": "Lunch",
    "description": "You need to eat something...",
    "daily": true,
    "active": true
  },
  "date": "2024-03-06",
  "startTime": "12:00",
  "duration": 30
}
```

### Daily Activity List

```json
{
  "date": "2024-03-05",
  "start": "09:00",
  "end": "17:00",
  "activities": ActivityItem[]
}
```

### Daily Recurring Activity / Ongoing Planned Task List

Full list of activities.

All activities with daily property set to true are _recurring_; when daily property is set to false the activity is considered to be _tasks_

The backend API should create the two arrays of recurring and tasks to be made available to the front-end application.

```javascript
export const createActivityLists (activitiesList) =>{
  // Initialise dailyRecurring and task lists
  let dailyRecurring = [];
  let tasks = [];
  // Read through all activities
  activitiesList.forEach((activity) => {
    if (activity.recurring) {
      dailyRecurring.push(activity);
    } else {
      task.push(activity);
    }
  });
  // Return both arrays of activities
  return (dailyRecurring, tasks);
}
```

## Angular Components

These are to made as class _Application_ models for use within the Angular application
to render the _Response_ models into usable data

### Activity Item

### Activity List

### Daily Activity
