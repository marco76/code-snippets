
### In the database is saved a date different from the date of the datepicker

This error is frequent when the date is passed to the backend via REST api.

When we are using a timezone defined time this one is converted by the REST service and the data saved in the backend differs 1 day from the date used in the frontend.

A simple approach to remove the issue is to convert the date in the frontend, e.g. using _moment.js_:

`dateUsedInTheCode.format('yyyy-MM-DD')` this removes the timezone and it avoids format errors. 
