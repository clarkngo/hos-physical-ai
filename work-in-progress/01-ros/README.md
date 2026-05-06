


# turtle sim
```
docker build -t ros-jazzy-turtle -f Dockerfile.turtle .
```
1. Prepare your Mac for the GUI

```
xhost +localhost
```

output:
```
clark@Clarks-MacBook-Air hos-physical-ai % xhost +localhost
localhost being added to access control list
```
2. Run the Turtle Container
```
docker run -it --rm \
    -e DISPLAY=host.docker.internal:0 \
    ros-jazzy-turtle
```    

3. Launch the Simulator

```
ros2 run turtlesim turtlesim_node
```

New terminal
```
docker ps
```

```
docker exec -it <CONTAINER_ID_OR_NAME> bash -c "source /opt/ros/jazzy/setup.bash && ros2 run turtlesim turtle_teleop_key"
```    

OR you can separate it:
```
docker exec -it <CONTAINER_ID_OR_NAME> bash
```

```
ros2 run turtlesim turtle_teleop_key
```

Run turtle sim
```
ros2 run turtlesim turtlesim_node
``
# rqt

requirement if no docker build yet:
```
docker build -t ros-jazzy-turtle -f Dockerfile.turtle_rqt .
```

Run rqt
```
rqt
```

New terminal 
```
docker exec -it <CONTAINER_ID> bash
```

Run turtle 2
```
ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel
```