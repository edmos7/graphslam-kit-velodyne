# graphslam-kit-velodyne
GraphSLAM implementation in Python for the KIT-Velodyne Dataset

Using the [KIT-Velodyne Dataset](https://www.mrt.kit.edu/z/publ/download/velodyneslam/dataset.html) i.e. LiDAR (point clouds) and Inertial (INS) sensor data mounted on a car, the goal is to obtain a consistent graph where nodes are the poses (position of the car in the world) at different time steps, as well as retrieve a map of the environment. This instance of Simultaneous Localization and Mapping (SLAM) is done offline (as opposed to online in real time).

- Built pose graph with nodes being absolute poses and edges being initial estimates of the relative transforms between subequent poses obtained from INS data
- Optimized the pose graph through the Levenberg-Marquardt method, this consists in finding the values for the absolute poses (nodes) while using the edges as constraints, where the goal is to minimize the difference between the predicted (initial estimate) transform and the "measured" i.e. registered/estimated transform (obtained through Iterative Closest Point, ICP)
- From the optimized poses the final map is built in order to visualize it, as well as the entire trajectory of the vehicle.

Files:

- graphslam.ipynb: The notebook where this all goes down, it can be run fully on Colab without any other requirement, though I suggest you skip execution of some cells (because they would take a long time); there are comments in the notebook to help you navigate it.
- map_trajectory.png: a PNG of the final map, if you want to view it without re-running the script (the PNG has anyhow been produced with the notebook script).
- point_cloud_stream.mp4: an MP4 video file (produced in the notebook) of the car's trajectory and registered point clouds mapping the environment, for an intuitive visualization.
- optimized_poses.pkl: a Pickle file of the optimized poses that you can load in the notebook, instea of re-running the entire optimization step.


@inproceedings{Moosmann2011IV,
        Address = {Baden-Baden, Germany},
        Author = {Frank Moosmann and Christoph Stiller},
        Booktitle = {Proceedings of the {IEEE} Intelligent Vehicles Symposium},
        Language = {english},
        Month = {June},
        Pages = {393--398},
        Title = {Velodyne {SLAM}},
        Url = {http://www.mrt.kit.edu/z/publ/download/Moosmann_IV11.pdf},
        Year = {2011},
        Bdsk-Url-1 = {http://www.kit.edu/z/publ/download/Moosmann_IV11.pdf}
}
  
