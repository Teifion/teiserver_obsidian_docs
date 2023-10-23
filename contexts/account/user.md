At the time of writing there are two implementations of users (which we are trying to combine).

There is a database backed `User` and an ETS backed `CacheUser`. In almost all realtime cases we are making use of the ETS backed user.