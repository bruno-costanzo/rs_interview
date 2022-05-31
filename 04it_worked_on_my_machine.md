# It worked on my machine

* The error is that all the instances of the model are being loaded only needing the IDs.

* This happens because a `{ .map }` method is used to get the IDs. This loads all instances of the model into memory.

* To correct this, a query must be made that brings only the ids of the bookings directly from the database. In addition, the `{ find_in_batches }` method could be used to avoid too heavy loads.

* These errors tend to be more noticeable in production environments because the DBs are denser.