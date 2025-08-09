# Dev Docs for Local Setup
Here are all details about setting up the project on local and some useful command for developer.

# Local Env Setup
Steps to setup the project on local:

1. Clone the repo on your system
2. Set git to ignore permission change
   - `git config core.fileMode false`
3. Executable permissions to d directory 
   - Inside project directory run `sudo chmod -R 777 d/`
4. Get the containers up and running
   - Inside your project directory in terminal, execute `d/start`
   - This command can take some up as it will be creating docker images and running the containers.
5. Next need to setup domain for local environment
   - Run `d/setup-ssl magento.test`
   - Then make sure there an entry like below in /etc/hosts file
     `127.0.0.1 magento.test`
     `127.0.0.1 magento.test`
     - If entry is missing please put it there manually 
6. Next step is to import database, here is the command to do so `d/mysql < path_to_my_sql_file_with_filename`
   - Some time sql file can cause identifier error and the fix for this is to clean up the sql file. 
   - Run this command cleanup the sql file `d/util/sql-file-cleanup <file_name_with_file_path>`
7. Setup env.php file
   - Inside app/etc directory, there's a file named **env.local.php**, duplicate the file and rename it to **env.php**
   - This file should have all the necessary configuration for local dev environment. 
8. Install composer dependencies `d/composer install`
9. Fix file permissions by running follwing commands
   - `d/fix-permissions && d/fix-own`
10. Execute magento commands `d/magento setup:upgrade`
11. Restart containers `d/restart` and hit **https://albarakmage.test** in browser.
12. That's it!

# Useful Commands:
Command to debug a script from terminal
d/xdebug php -d xdebug.start_with_request=yes pup/dev-script.php

# Todos:
- Available commands documentation
- xdebuger setup for developer
- Command to reset admin user password
- Live reloader for frontend work
