Automate your WordPress development workflow.
# INSTALL 

cd wordpress-docker

cp env.config .env

docker-compose build

docker-compose up

# BACKUP WORDPRESS BY CLI
docker-compose exec -it [db] mysqldump -u [user] -p[password] [database] > [file.sql]

docker exec -it wordpress-docker_db_1 mysqldump -u root -p root wordpress > zaloha.sql

#RESTORE DB

cat zaloha.sql | docker exec -i wordpress-docker_db_1 mysql -u root -proot wordpress

# BACKUP FILE SYSTEM
tar cvfz wordpress.tar.gz build/wordpress

# RESTORE FILE SYSTEM
tar xvfz wordpress.tar.gz -C build/wordpress

# CHANGE URL BY WP-CLI
docker-compose run --rm wpcli wp search-replace {OLD_URL} {NEW_URL} --all-tables
