**Project Overview**: (https://github.com/abishek-socrates/Mediawiki/assets/170268442/d6726557-069e-4ac4-93f4-0c23e99a450d)

**1. Dockerfiles**
* Application Dockerfile - For installing and configuring Mediawiki on a Centos7 container.
* Mariadb Dockerfile`  - For installing and configuring Mariadb for handling Mediawiki database.

**2. Docker hub**
The application and database images are pushed to docker hub.

**3. Helm Chart and Kubernetes**
The kubernetes objects are defined in following files: `mediawiki-deployment.yaml` `mediawiki-service.yaml` `db-deployment.yaml` `db-service.yaml` `env-configmap.yaml` `wikinetwork-networkpolicy.yaml` `secret.yaml`

`secret.yaml` file is created for storing base64 converted password string to be used for variable MYSQL_ROOT_PASSWORD.
Replace the encrypted string by generating a new string using command: `echo -n "<new_password>" | base64`

**4. Deploying the Stack**

helm install mediawiki ./{The helm chart name}

Configure the Mediawiki by providing the values as below:
* Database Host : `db:33060`
* Database Name : `wikidatabase`
* Database Username : `root`
* Database Password : `Passw0rd`

**5. After the DB connections are setup, provide details for setting up your new Wiki.**

**6. After final submission you it will generate a LocalSettings.php file which needs to be copied on the mediawiki container at location: `/opt/rh/httpd24/root/var/www/html/mediawiki`**.

