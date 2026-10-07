# Patch Exercise Notes

## Changes Made

1. Fixed the SQL status filter in `TaskRepository.java` by grouping the title/description OR condition so the status filter is applied correctly.
2. Removed the artificial `Thread.sleep()` delay from `TaskController.java` to avoid unnecessary request latency.
3. Reset pagination to page 1 whenever the search or status filter changes in `App.jsx`.
4. Added validation for `page` and `pageSize` in `TaskController.java` and return HTTP 400 for invalid values.
5. Fixed the frontend loading state in `useTasks.js` so failed API requests do not leave the UI stuck in loading.

## What I Chose Not to Change

- The backend loads all matching tasks and performs pagination in Java. Database-level pagination would be more scalable for a large dataset.
- Invalid status values can result in an unhandled exception instead of a clean 400 response.
- The frontend could have stale responses if multiple requests complete out of order.

I prioritized the issues directly affecting the current application's correctness, responsiveness, and user-visible behavior.

## Biggest Remaining Risk

The backend currently loads all matching tasks and performs pagination in Java. This could become inefficient with a large dataset because database-level pagination would scale better.

## Tools / AI Usage

I used ChatGPT assistance to identify potential bugs and understand their root causes. I reproduced the issues locally, verified the behavior, and reviewed and tested each proposed fix before accepting it.
