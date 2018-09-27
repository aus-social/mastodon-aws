* Shut down server
* Take AMI Image of server (Consider EBS Snapshot)
* Take backup of DB

* Start up server again
* Apply server patches
* Reboot if kernel patches

* `git fetch`
* `git stash`
* `git checkout <version>`
* `git stash pop`
* edit docker-compose.yml if required
* `docker-compose build`
* `docker-compose run --rm web bundle exec rake db:migrate` (optional) 
* `docker-compose run --rm web bundle exec rake assets:precompile` (optional)
* `docker-compose up -d`

Notice: The process does not require `docker-compose down` because the docker-compose build will create the image in the background and docker-compose up -d will upgrade automaticly.


