# cd into the root folder

sudo chown -R 10001:65533 $(pwd)

# To create a docker image and run a container in detached mode

V_PATH=$(pwd); docker run -it --rm --name verdaccio \
 -p 4873:4873 \
 -v $V_PATH/conf:/verdaccio/conf \
 -v $V_PATH/storage:/verdaccio/storage \
 -v $V_PATH/plugins:/verdaccio/plugins \
 --name verdaccio \
 verdaccio/verdaccio

docker run -it --detach \
--publish 4873:4873 \
--volume `pwd`/conf:/verdaccio/conf \
--volume `pwd`/storage:/verdaccio/storage \
--volume `pwd`/plugins:/verdaccio/plugins \
--name verdaccio \
verdaccio/verdaccio

<!-- --env "VERDACCIO_APPDIR=/opt/verdaccio"
--env "VERDACCIO_USER_NAME=verdaccio"
--env "VERDACCIO_USER_UID=10001"
--env "VERDACCIO_PORT=4873"
--env "VERDACCIO_PROTOCOL=https" -->

# To run the container with default verdaccio image

docker run -it --rm --name verdaccio -p 4873:4873 verdaccio/verdaccio

# npm adduser --registry http://localhost:4873/

username: christopherpaul
password: christopherpaul
email: christopher.paul@trell.in
