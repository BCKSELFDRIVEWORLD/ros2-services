# ros2-services

Like Topics, Services are also a method of communication between nodes for ROS2. So, to understand them better, compare them with something you already know. Topics use the publisher-subscriber model. On the other hand, Services use a call-response model. As you saw, you can subscribe a node to a Topic to receive particular information with continuous updates. At the same time, a Service only provides data when called explicitly by a Client.

Understand all this in a better way through the following example. Think about a face recognition system. The best approach will be to provide it using a Service. Then, your ROS2 program will call that Service (send a request to the Service) every time it needs the name of the person your recognition system has in front of it. Then, the Service will return a response providing the person's name.

And why is it better to use a Service in this case? Well, because you do not need to constantly run your face detection node when there is nobody around the robot. It would be a massive waste of resources. You only need to run it when there is a person in front of the robot.

Working with Services, you will have two sides: Clients and Servers. You can have multiple Clients using the same Service Server, but you can only have one Server for one Service.

![image](https://github.com/BCKSELFDRIVEWORLD/ros2-services/assets/146545020/81d808ea-bf88-44f2-8144-4ce795331e17)


# Basic Service Commands


      source /opt/ros/humble/setup.sh
      ros2 service list
      ros2 service call <service_name> <service_type> <value>
      ros2 service type /moving
      ros2 interface show std_srvs/srv/Empty
      ros2 interface show std_srvs/srv/SetBool
      ros2 service call /moving std_srvs/srv/Empty
      ros2 service call /stop std_srvs/srv/Empty


As you have seen, you can use the ros2 service call command to emulate a Client without creating a new program, which is especially useful for testing a given Service. However, as your ROS2 application gets bigger and takes shape, you will need to implement a Client that can interact with a Service from their nodes, and this is what you will see in the next sections.

# Create a Service Client

          cd ~/ros2_ws/src
          ros2 pkg create client_pkg --build-type ament_python --dependencies rclpy std_srvs
          


