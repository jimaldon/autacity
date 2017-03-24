Udacity is using a new dataset production method that allows for quick processing and release cycles. Instead of spending weeks (or months) waiting on 3D annotation data to be produced by third-party companies, we have elected to try out something new that enables datasets to be released immediately after they are recorded. While we do lose some sample distribution on each individual dataset due to the same obstacles being used for each session, the massive speedup in production and reduction in cost allows us to release new datasets daily (and with different obstacles with each session). In this manner, we can directly control the type of data being recorded so that we can cover all situations without hoping for them to happen on real roads, and we have extreme precision on obstacle location with differential RTK GPS technology.

Due to this new approach, there are some major differences from the Kitti datasets. It is important to note that recorded positions are recorded with respect to the base station, not the capture vehicle. The NED positions in the rtkfix topic are therefore in relation to a FIXED POINT, NOT THE CAPTURE OR OBSTACLE VEHICLES. The relative positions can be calculated easily, as the NED frame is cartesian space, not polar. The XML tracklet files will, however, be in the frame of the capture vehicle. This means that the capture vehicle is also included in the recorded positions, and is denoted by the ROS topic ‘/gps/rtkfix’ in this first dataset. The single obstacle vehicle in this dataset is located in the 'obs1/' topic namespace, but this will be changed to '/obstacles/obstacle_name' in future releases to accomodate the creation of XML tracklet files for multiple obstacles. Orientation of obstacles are not evaluated in Round 1, but will be evaluated in Round 2. The pose section of the ROS bags included in this release IS NOT A VALID QUATERNION, and does not represent either the pose of the capture vehicle or the obstacle.

As we are still working this new method of data collection, this first release has some important quirks to take note of while developing your solution. There is no XML tracklet file included with these datasets. They will be released as soon as they are available, in conjunction with the opening of the online leaderboard. Also, we have included the "Noisy" folder, which has partially useable data that we collected, but most likely has unuseable position information. The camera, radar, and LIDAR data is still present, and may prove useful. Additionally, this will be the only dataset with the '/velodyne_points' topic. To save bandwidth, future releases will only include the '/velodyne_packets' and the standard Velodyne ROS driver will need to be used to create the points data.

Good luck!

Dataset Information:

types:       bond/Status                           [eacc84bf5d65b6777d4c50f463dfb9c8]
             diagnostic_msgs/DiagnosticArray       [60810da900de1dd6ddd437c3503511da]
             diagnostic_msgs/DiagnosticStatus      [d0ce08bc6e5ba34c7754f563a9cabaf1]
             dynamic_reconfigure/Config            [958f16a05573709014982821e6822580]
             dynamic_reconfigure/ConfigDescription [757ce9d44ba8ddd801bb30bc456f946f]
             nav_msgs/Odometry                     [cd5e73d190d741a2f92e81eda573aca7]
             radar_driver/RadarTracks              [6a2de2f790cb8bb0e149d45d297462f8]
             rosgraph_msgs/Log                     [acffd30cd6b6de30f120938c17c593fb]
             sensor_msgs/Image                     [060021388200f6f0f447d0fcd9c64743]
             sensor_msgs/NavSatFix                 [2d3a8cd499b9b4a0249fb98fd05cfa48]
             sensor_msgs/PointCloud2               [1158d486dd51d683ce2f1be655c3c181]
             sensor_msgs/Range                     [c005c34273dc426c67a020a87bc24148]
             sensor_msgs/TimeReference             [fded64a0265108ba86c3d38fb11c0c16]
             tf2_msgs/TFMessage                    [94810edda583a504dfda3829e70d7eec]
             velodyne_msgs/VelodyneScan            [50804fc9533a0e579e6322c04ae70566]
topics:      /cloud_nodelet/parameter_descriptions     : dynamic_reconfigure/ConfigDescription
             /cloud_nodelet/parameter_updates          : dynamic_reconfigure/Config           
             /diagnostics                              : diagnostic_msgs/DiagnosticArray       (3 connections)
             /diagnostics_agg                          : diagnostic_msgs/DiagnosticArray       (2 connections)
             /diagnostics_toplevel_state               : diagnostic_msgs/DiagnosticStatus      (2 connections)
             /gps/fix                                  : sensor_msgs/NavSatFix                
             /gps/rtkfix                               : nav_msgs/Odometry                    
             /gps/time                                 : sensor_msgs/TimeReference            
             /image_raw                                : sensor_msgs/Image                    
             /obs1/gps/fix                             : sensor_msgs/NavSatFix                
             /obs1/gps/rtkfix                          : nav_msgs/Odometry                    
             /obs1/gps/time                            : sensor_msgs/TimeReference            
             /radar/points                             : sensor_msgs/PointCloud2              
             /radar/range                              : sensor_msgs/Range                    
             /radar/tracks                             : radar_driver/RadarTracks             
             /rosout                                   : rosgraph_msgs/Log                     (7 connections)
             /tf                                       : tf2_msgs/TFMessage                   
             /velodyne_nodelet_manager/bond            : bond/Status                           (3 connections)
             /velodyne_packets                         : velodyne_msgs/VelodyneScan           
             /velodyne_points                          : sensor_msgs/PointCloud2

