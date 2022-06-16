# args


To configure this tool run the following command:


curl https://raw.githubusercontent.com/haxxxer/args/main/configure.sh | bash



The command above will do the following:

- download args.sh file
- give it execute permission 
- move it to /usr/local/bin as "args" so that you can run it from everywhere without extension!



Examples:

- args -e email "$@" 


use this commmand inside your script.




if "-e" was passed with your script, the command above will return the value right next to it

if "-e" was not passed, the exit code will be 1

if "-e" was passed but does not match  email pattern, the exit code will be 2


if you want args to just get the flag value without applying a pattern restrection, replace email with any
- args -e any "@"

There are 4 patterns provided with args by default:

- email
- ip
- url
- host (matches supdomains and domains) 
- phone


you can edit the script and add your own patterns using regex


you can test the command from outstide the script as follows:

	args -p phone "-i hello -p 055-555-5555"

this should return the value of : 055-555-5555


where as this command: args --ip ip "--ip 9.9.9.99999"

should return a status code of: 2 because the value of --ip is not valid ip address (Check status code with: echo $?)

