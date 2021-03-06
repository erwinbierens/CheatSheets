Forever Cheatsheet
--------------------------------
A simple CLI tool for ensuring that a given script runs continuously (i.e. forever).


[+] Installation
## You could install forever using npm like this:
sudo npm install -g forever

[+] Commands

## And then start your application with:
forever server.js

## Or as a service:
forever start server.js

## Forever restarts your app when it crashes or stops for some reason. To restrict restarts to 5 you could use:
forever -m5 server.js

## To list all running processes:
forever list

## Note the integer in the brackets and use it as following to stop a process:
forever stop 0

## Restarting a running process goes:
forever restart 0

## If you're working on your application file, you can use the -w parameter to restart automatically whenever your server.js file changes:
forever -w server.js
