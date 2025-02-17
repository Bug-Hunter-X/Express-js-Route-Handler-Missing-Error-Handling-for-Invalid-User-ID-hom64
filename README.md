# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid input. Specifically, it showcases a scenario where a route handler expects a numeric user ID but doesn't handle cases where a non-numeric ID is provided.

## Bug Description

The `/users/:id` route handler attempts to parse the `userId` as an integer using `parseInt()`. However, if `userId` is not a valid integer (e.g., a string or a non-numeric value), `parseInt()` returns `NaN`, leading to unexpected behavior or application crashes.  The bug is the absence of a check for `isNaN()` to handle this. 

## Solution

The solution involves adding error handling to check if `parseInt(userId)` results in `NaN`.  If it does, the handler will return an appropriate error response, preventing crashes and enhancing the application's robustness.

## How to reproduce

1. Clone this repository.
2. Run `npm install` to install Express.js.
3. Run `node bug.js`.
4. Send a request to `/users/abc` (or any non-numeric ID).  You'll see the app crash or unexpected behavior.
5. Run `node bugSolution.js`. This version includes the fix, which should return a proper 400 status code response.
