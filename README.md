# Mnesia---Smalldatabase-for-events
this small database  works as basic CRUD(Create, Retrieve, Update, Delete).

This time I created a much simpler and basic crud(create, retrieve, update, delete) like database.
In computer programming, create, read, update and delete are the four basic functions of persistent storage.
This time i created only one table(events), in which we can add all the events we have.
I used to store my tables on disc({disc_copies, NodeList}) all the time, it helps me to get the backups.

Now, the functions in this examples
--------------------------------------

##Functions...
---------------------

### 1. init().
     In this function, 3 things defined
        >> Create a schema (It is a special table contains informations about tables and each tables storage type etc),
        >> Starts the schema (mnesia:start_schema()),
        >> And created our table(events).
        
### 2.insert_event().
    This function takes four arguments corresponding to the record entry , name_of_ the event(birthday, meeting, appointments etc), wHen to shows the date,
    wHere is the location and wHat is for giving small description("dinner at 7pm with X"). and add all them to table using mnesia:write().
  
### 3.retrieve_all().
    For retrieving all the events in the table, by using qlc(query list comprehensions),this module implements a query interface.
    
### 4.retrieve_per_date().
    In this function,we retrieve event details of corresponding date. By using qlc module, we match the Date attribute with the
    #events.date and retrieve details

### 5. todays_events().
    We use the same module and match our date attribute with current date(erlang:date()).
    
### 6. bdays_only().
    Filtered out the birthday events only from our table by giving name_of_event = birthday.
    
### 7. edit().
      This function is one of the important one our daatabase. We define an event for a date, and we can change the events details
      by using the edit function.
      I define two other functions inside it(delete, update). So, first we search for a match in the given date. If we found any
      events declared on the date, if we want to edit it, first delete the event and then updated it.
      
### 8.update_table().
     Here we recursively call the events on the given date, and change our table entries as we need.
     
### 9.delete().
     First find the events on the date we choose, then iterate over each event using lists:foreach/2 and call mnesia:delete_object().
     
### 10.events_for_set_days().
      I define this function for collect all events for a set of days,it is not a perfect function. But i define this for providing
      my idea. I take two days Day1 and DayN and created a list of numbers between this(lists:seq(Day1, DayN)), then pass each as the Day
      for our date({Year,Month,Day}),and recursively find match for dates, and retrieve corresponding events.It is not perfectly
      implemented
      
#### This is what our simple database do.

Now i starts to learn the OTP framework and the cowboy to define a REST api.
