# University Planner App: Automate Your Academics!

This README provides an overview of the **University Planner**, a web application designed to streamline your academic life by seamlessly integrating with your Canvas account.

## Key Features:

- **Direct Canvas Integration**: Syncs directly with your Canvas account, automatically importing data like:
  - Exam dates
  - Assignment deadlines
  - Lecture and discussion times
  - Announcements
  - And more!

- **Integrated Calendar**: Effortlessly add all imported information to a customizable calendar, giving you a clear overview of your schedule.

- **Reduced Manual Work**: No more manually entering deadlines or struggling to remember exam dates. This app keeps you organized and informed.

- **Easy to Use**: Intuitive interface allows for seamless navigation and interaction with your academic data.

## Getting Started:

### Prerequisites:
- A Canvas account
- Access to a web browser

### Installation:

#### How to install dependencies for my app:

Open your terminal to the app's root directory, and input the following command:

```
bash
cd node-express
```
Next, input the following command to install all the dependencies:
```
npm install --save express sqlite3 md5 node-fetch ical.js nodemon bcrypt passport express-flash express-session method-override passport-local dotenv
```

How to run the server

To run the server without monitoring changes in javascript files, simply do:
```
npm run server
```
(For devs only) to run the server with monitoring changes in javascript files so that it automatically restarts every time 
there is a change, simply do:
```
npm run server-dev
```
The purpose of databaseAPI.js
Any javascript files in the public/js folder are served to the server, but they cannot have direct access to our database. In other words, the scripts on the server cannot directly query, insert, update, delete, etc. on our sqlite3 database.

To solve this problem, we need a "middle man" API, and databaseAPI.js is exactly this. It uses the browser's built in fetch() API to communicates with the database's public endpoints (as defined in SECTION 6 of main.js) and query the database via those. To help with readability, I have abstracted these fetch() requests and made different functions to query the database. Please read the section below on how to use them in your scripts stored in public/js folder.

How to use databaseAPI.js

First, put the following line at the top of the script that wants to access the database:
```
import * as dbAPI from "./databaseAPI.js"
```
To query (get) something from the database, simply do:
```
let returnData = dbAPI.queryFunction(theItemYouWantToQuery) // 
```
Pseudo-code
Ex: I want to query all today events for the currently logged 
in user, I simply do:
```
let returnData = dbAPI.queryTodayEvents();
```
where returnData is an ARRAY OF OBJECTS (console.log(returnData) for more information)

Feel free to checkout databaseAPI.js for more available querry functions you can call. If you need a specific function in databaseAPI.js to cater to your needs, please let the backend team know.

## Authorization:
Follow the prompts to link your Canvas account to the University Planner.
Enjoy!
Start managing your academic life with ease!

## Contributing:

This project is private.

## Additional Notes:
