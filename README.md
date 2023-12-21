# Create your self-built Docker Moodle testing environment + CodeRunner 

This repository, forked from [dmfama20](https://github.com/Dmfama20/docker_moodle_minimal/tree/master) provides a minimal Moodle testing environment based on docker compose, with the inclusion of a JobeInABox container that can be used with the CodeRunner plugin.

## Disclaimer

This deployment is **NOT** intended for a production environment. 
It is an reference implementation aimed at Moodle testers.

## How to start
1.) Clone this repository inside a folder

``git clone https://github.com/Dmfama20/docker_moodle_minimal.git minimal_moodle``

2.) cd into the project folder and create an empty folder called *moodledata*

3.) Place your favourite moodle version in a folder called *moodle*. You can get it from [moodle.org](https://download.moodle.org/releases/latest/). Since the PHP container is PHP7.4, the latest version of Moodle you can install is 4.1.x

4.) docker-compose up -d

5.) Install moodle via browser 

OR

via CLI (if available):

``docker exec -it docker_moodle-app  php admin/cli/install.php --lang=en --wwwroot=localhost --dataroot=/var/www/moodledata --dbtype=mariadb --dbhost=docker_moodle-db  --dbname=moodle --dbuser=moodledude --dbpass=mysecretpassword --prefix=mdl_ --fullname=moodle_minimal --shortname=moodle_minimal --adminpass=test --adminemail=admin@moodle.invalid --agree-license --non-interactive``

6.) Visit your moodle at http://localhost:8088

7.) Use the Moodle plugin repository to install the plugins *qbehaviour_adaptive_adapted_for_coderunner* and *qtype_coderunner*.

8.) Configure the CodeRunner question type, setting the Jobe host to *docker-moodle-jobe*

