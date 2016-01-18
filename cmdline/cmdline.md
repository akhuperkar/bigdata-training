## Unix Command Line Exercises
1. `mkdir`, `cd`, `TAB`, `CTRL+L`

    Create a directory called `cmdline` and step into it

    `mkdir cmdline`

    `cd cmdline`  

* `cd ..` `cp`

  Copy the `birdstrikes.csv` into the training directory

  `cd ..`

  `cp birdstrikes.csv cmdline`

  `cd cmdline`

* `less`

  Explore the csv  

  `less birdstrikes.csv`

* `head`

  Print the first 10 lines to the file to the screen

  `head birdstrikes.csv`

  `head -n 10 birdstrikes.csv`   

  id,aircraft,flight_date,damage,airline,state,phase_of_flight,reported_date,bird_size,cost,feet_above_ground

  2,Airplane,2000-01-01,No damage,CONTINENTAL AIRLINES,New Jersey,Take-off run,,Medium,0,0

  3,Airplane,2000-01-01,No damage,UNITED AIRLINES,,,,Medium,0,

  4,Airplane,2000-01-01,No damage,UNITED AIRLINES,Colorado,Climb,,Medium,0,

  5,Airplane,2000-01-01,No damage,UNITED AIRLINES,Illinois,Approach,,Medium,0,

  7,Airplane,2000-01-01,Caused damage,US CUSTOMS AND BORDER PROTECTION,Florida,En
  Route,,Large,0,1000

  8,Airplane,2000-01-01,No damage,AMERICAN AIRLINES,,Take-off run,2000-01-01,Small,0,0

  9,Airplane,2000-01-02,No damage,BUSINESS,Ohio,Landing Roll,,Small,0,0

  10,Airplane,2000-01-02,No damage,BUSINESS,Florida,Approach,,Medium,0,2000

  11,Airplane,2000-01-02,No damage,UNITED AIRLINES,California,Take-off run,,Small,0,0

* `man`

  What is `-n`? Check it in the manual

  `man head`  

* `tail`

  Check the last 10 lines of the file

  `tail birdstrikes.csv`

  `tail -n 10 birdstrikes.csv`

  99363,,2011-12-28,No damage,UNKNOWN,Kentucky,,,Small,0,

  99377,,2011-12-29,No damage,UNKNOWN,Nevada,,,,0,

  99378,,2011-12-29,No damage,UNKNOWN,Illinois,,,Medium,0,

  99380,,2011-12-29,No damage,UNKNOWN,California,,,Small,0,

  99385,,2011-12-30,No damage,UNKNOWN,Washington,,,,0,

  99386,,2011-12-30,No damage,UNKNOWN,Texas,,,Medium,0,

  99399,,2011-12-31,No damage,UNKNOWN,Ohio,,,Medium,0,

  99400,,2011-12-31,No damage,UNKNOWN,Ohio,,,Small,0,

  99402,,2011-12-31,No damage,UNKNOWN,Missouri,,,Small,0,

  99405,,2011-12-31,Caused damage,PRIVATELY OWNED,California,Approach,2012-02-07,,8000,3

* *Exercise*: Check the last line of the file

  `tail -n 1 birdstrikes.csv`

  `tail -1 birdstrikes.csv`

* Put the first 10 lines into another file

  `head -n 10 birdstrikes.csv > first10.csv`

* *Exercise*: Show the 10th line of the csv

  `tail -1 first10.csv`

  11,Airplane,2000-01-02,No damage,UNITED AIRLINES,California,Take-off run,,Small,0,0

* *Exercise*: Show the 5th line of the csv

  `head -n 5 birdstrikes.csv > first5.csv`

  `tail -1 first5.csv`

  5,Airplane,2000-01-01,No damage,UNITED AIRLINES,Illinois,Approach,,Medium,0,

* Above using `|` operator

  `head -5 birdstrikes.csv | tail -1`  

  5,Airplane,2000-01-01,No damage,UNITED AIRLINES,Illinois,Approach,,Medium,0,

* *Excercise*: Put the 5th line into the 5thline.csv

  `head -5 birdstrikes.csv | tail -1 > 5thline.csv`

  `cat 5thline.csv`

  5,Airplane,2000-01-01,No damage,UNITED AIRLINES,Illinois,Approach,,Medium,0,

* `grep`

  Filter rows to only show incidents from California

  `cat birdstrikes.csv | grep California | head -5`

  11,Airplane,2000-01-02,No damage,UNITED AIRLINES,California,Take-off run,,Small,0,0

  23,Airplane,2000-01-04,No damage,AMERICAN AIRLINES,California,Climb,,Large,26727,100

  31,Airplane,2000-01-05,No damage,NORTHWEST AIRLINES,California,Take-off run,,Medium,0,0

  40,Airplane,2000-01-06,No damage,AMERICA WEST AIRLINES,California,Approach,2000-01-06,Small,0,

  50,Airplane,2000-01-08,No damage,UNITED AIRLINES,California,Take-off run,,Medium,0,0

* `grep -v`

  Only show incidents NOT with Airplanes

  `cat birdstrikes.csv | grep -v Airplane | head -3`

  id,aircraft,flight_date,damage,airline,state,phase_of_flight,reported_date,bird_size,cost,feet_above_ground

  28,Helicopter,2000-01-04,No damage,PHI INC,,Approach,2000-01-04,,0,100

  115,Helicopter,2000-01-14,Caused damage,BUSINESS,California,Approach,2000-01-15,,1438,800

* *Exercise*: Show the first 3 Helicopter incidents NOT in Colorado

  `cat birdstrikes.csv | grep Helicopter | grep -v Colorado | head -3`

  28,Helicopter,2000-01-04,No damage,PHI INC,,Approach,2000-01-04,,0,100

  115,Helicopter,2000-01-14,Caused damage,BUSINESS,California,Approach,2000-01-15,,1438,800

  341,Helicopter,2000-02-17,Caused damage,BUSINESS,Alabama,Approach,2000-02-17,,67,500

* `grep -i`

  Ignore case

  `cat birdstrikes.csv | grep -i airplane | head -2`

  2,Airplane,2000-01-01,No damage,CONTINENTAL AIRLINES,New Jersey,Take-off run,,Medium,0,0

  3,Airplane,2000-01-01,No damage,UNITED AIRLINES,,,,Medium,0,

* `cut`

  Display only the *aircraft* and the *flight_date* columns

  `cat birdstrikes.csv | cut -d, -f 2,3 | head -3`

  aircraft,flight_date

  Airplane,2000-01-01

  Airplane,2000-01-01

* *Excercise*: Display only the *state* and the *bird_size* columns of Airplane accidents

  `cat birdstrikes.csv | grep Airplane | cut -d, -f 6,9 | head -3`

  New Jersey,Medium

  ,Medium

  Colorado,Medium

* `sed 1d`

  `cat birdstrikes.csv | head -3`

  id,aircraft,flight_date,damage,airline,state,phase_of_flight,reported_date,bird_size,cost,feet_above_ground

  2,Airplane,2000-01-01,No damage,CONTINENTAL AIRLINES,New Jersey,Take-off run,,Medium,0,0

  3,Airplane,2000-01-01,No damage,UNITED AIRLINES,,,,Medium,0,

  Display top-3 rows without a header

  `cat birdstrikes.csv | sed 1d | head -3`

  2,Airplane,2000-01-01,No damage,CONTINENTAL AIRLINES,New Jersey,Take-off run,,Medium,0,0

  3,Airplane,2000-01-01,No damage,UNITED AIRLINES,,,,Medium,0,

  4,Airplane,2000-01-01,No damage,UNITED AIRLINES,Colorado,Climb,,Medium,0,

* `wc` -

  Show the line, word and character count of birdstrikes

  `wc birdstrikes.csv`

  99405  307242 7598090 birdstrikes.csv

* *Exercise*: Show the word, line and character count of the first 10 lines

  `head birdstrikes.csv | wc`

  10      35     822

* *Excercise*: How many incidents were in California (only output line count)

  `cat birdstrikes.csv | grep California | wc -l`

  7803
