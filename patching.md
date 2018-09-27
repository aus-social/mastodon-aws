## Server Patching Procedure (Outage window required)

>* Shut down server
>* Take AMI Image of server
>* Take backup of DB (RDS Snapshot is online backup)
>* Start up server again
>* Apply server patches
>* Reboot if kernel patches

## Mastodon Docker Live Upgrade Procedure (Limited outage window required)

>* Read the upgrade details - the Docker specific details are generally documented by Gargron.
>* `git fetch`
>* `git stash`
>* `git checkout <version>`
>* `git stash pop`
>* edit docker-compose.yml if required (pop should restore the docker-compose.yml)
>* `docker-compose build`
>* `docker-compose run --rm web bundle exec rake db:migrate` (optional) 
>* `docker-compose up -d`

Notice: The process does not require `docker-compose down` because the docker-compose build will create the image in the background and docker-compose up -d will upgrade automaticly.


