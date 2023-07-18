# matomo-docker
Docker-compose setup for restoring a Matomo backup from an SQL data dump

## Usage

### Obtain a backup of the Matomo database
These steps are specific to my Matomo host. You should follow whatever steps are needed to obtain a .sql backup file of your Matomo database.

1. Visit: https://cp.s814.sureserver.com/archive/index.php
2. Tick the 'MySQL 8' row
3. Click 'Back up now'. If this option is disabled, it could be due to the daily backup limit being reached. In which case continue on the next step as a recent backup should already exist.
4. Select 'OK' to "Any existing backups, including saved ones, will be overwritten. Are you sure you want to continue?"
5. Click on the "Download Backups" tab and wait for the backup file to appear in the list in the 'MySQL 8' row.
6. Click on the "Download file mysql8.tar.gz" link
7. Extract "mysql8.tar.gz"
8. If 2x .sql files are extracted, you will need to use the larger one (it should be several MB in size) to restore from.

### Prepare the Matomo backup
These steps will prepare this Matomo environment to restore the backup.

1. Copy your Matamo backup .sql file to the ./scripts dircectory of this project. 
2. Add `USE 'matomo';` to the very top of the .sql file you just added to the ./scripts directory

### Check the Docker Environemnt
It is important that the Matomo and MYSQL versions in both the backed up environment and this Docker environment match. To Check this:

1. TODO

### Start the Matomo Docker environment

1. Run "docker-compose up" from the root of this project
2. Wait for everything to start up
3. Visit http://0.0.0.0:8080/
4. Click "Next"
5. Scroll to bottom and click "Next"
6. Click "Next"
7. Click "Reuse the existing tables"
8. Scroll to bottom and click "Continue to Matomo"
9. Login with the username and password that you use to connect to the original Matomo server that you took the backup from.
10. You should now see the Matamo dashboard with your data running.
