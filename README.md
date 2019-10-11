Simple Selenium Set up in  Docker Swarm Cluster:
-----------------------------------------------

Initializing the Manager Node and run this command on one of the hosts for Docker Swarm mode on the same,

[master]$ docker swarm init --advertise-addr <manager-ip>

or

[master]$ docker swarm init

Then, other two machines execute the join the command

[slave1]$ docker swarm join --token SWMTKN-1-26pq77zp55lor9wxjoyp1dv454xw53t65655rzzvoqxhpp3ins93-au7xwjaw6x2gwyvy5mqygd66n 192.168.0.2:2377

[slave2]$ docker swarm join --token SWMTKN-1-26pq77zp55lor9wxjoyp1dv454xw53t65655rzzvoqxhpp3ins93-au7xwjaw6x2gwyvy5mqygd66n 192.168.0.2:2377

Once executed the command view the information on the master node,

[master]$ $ docker info

Node information,

[master]$ docker node ls

Deploying the Selenium selenium_grid 

[master]$ docker stack deploy --compose-file docker-swarm-selenium.yaml selenium_grid

Now we can check status of our stack using the stack ps command

[master]$ docker stack ps selenium_grid

Your selenium_grid is working now on docker swarm. If you would like to scale the grid nodes use the scale command

[master]$ docker service scale grid_chrome=5

[master]$ docker service ls






