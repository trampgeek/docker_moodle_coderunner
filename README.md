# Create your self-built Docker Moodle testing environment + CodeRunner 

This repository, forked from [dmfama20](https://github.com/Dmfama20/docker_moodle_minimal/tree/master) provides a minimal Moodle testing environment based on docker compose, with the inclusion of a JobeInABox container that can be used with the CodeRunner plugin.

## Disclaimer

This deployment is **NOT** intended for a production environment. 
It is an reference implementation aimed at Moodle testers.

## How to start
1.) Clone this repository inside a folder

``git clone https://github.com/trampgeek/docker_moodle_coderunner.git``

2.) cd into the project folder and create an empty folder called *moodledata*. Make it writeable by www-data.

3.) Place your favourite moodle version in a folder called *moodle*. You can get it from [moodle.org](https://download.moodle.org/releases/latest/). Since the PHP container is PHP8.1, you will need
to use a recent version of Moodle, V4.1 or later.

4.) Make the entire moodle filetree writeable and searchable by user www-data.

5.) docker-compose up -d

6.) Visit your moodle at http://localhost:8088

7.) Install moodle via browser, setting:
    * DB type: mariadb
    * DB host: docker_moodle-db
    * DB name: moodle
    * DB user: moodledude
    * DB pass: mysecretpassword

8.) Use the [Moodle plugin repository](https://moodle.org/plugins/) to install the plugins *qbehaviour_adaptive_adapted_for_coderunner* and *qtype_coderunner*.

9.) Configure the CodeRunner question type, setting the Jobe server to *docker-moodle-jobe*

10.) Go to Sit administration > General > HTTP Security and delete the following entries from the *cURL blocked hosts list*:
    * 127.0.0.1
    * 192.168.0.0/16
    * localhost

11.) Start writing CodeRunner questions!