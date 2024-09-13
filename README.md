# Presentation

Here is the repository dedicated to properly launching the TIAGO robot simulation. \
This repository contains all the necessary files to simulate the behavior of TIAGO, a mobile robot with a wheeled base. The simulation process relies on various repositories provided here, each containing specific configurations 
and assets required for the simulation to work seamlessly. 


The repositories are named from 1 to 7, and they need to be placed in the src directory of your ROS (Robot Operating System) workspace. 
Once these files are correctly positioned, you will be able to simulate TIAGO's movements.

# Installation

The first thing to do is to create a worskapce : 

<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>cd ~/TIAGO_perso
mkdir ~/TIAGO_perso/src
cd ~/TIAGO_perso/src
git clone https://github.com/Loic-Barthe/TiagoLAAS.git
cd ~/TIAGO_perso
rosdep install --from-paths src</code>
</pre>




Then, it is necessary to place all packages in the src of your worspace. The src directory should be organized as follows, as shown in the picture bellow. 


<div style="text-align: center;">
    <img src="https://github.com/Loic-Barthe/TiagoLAAS/raw/main/file_source.png" width="50%" alt="file_source">
</div>



Unzip the repos_x files and place them into an already existing workspace. To create a workspace 

There are also two missing packages, as shown in the previous image: Pinocchio and Crocoddyl. These two packages are essential for the simulation and can be installed either in debug mode, 
allowing you to use tools like GDB for debugging, or through ROBOTPKG.


## ROBOTPKG Installation

To install ROBOTPKG, check the website : http://robotpkg.openrobots.org/debian.html and follow instructions.

#### Warning !

However, if you choose to install the packages via ROBOTPKG, you'll need to adjust your environment variables accordingly. The necessary changes are outlined in detail in my report.


<div style="text-align: center;">
    <img src="https://github.com/Loic-Barthe/TiagoLAAS/raw/main/env_var.png" width="50%" alt="file_source">
</div>



[Report] https://github.com/Loic-Barthe/TiagoLAAS/blob/main/Rapport_TIAGO_Simulation_LAAS.pdf


# Build

After cloning the repository into the src folder of the workspace and navigating to the root of the workspace, run the following command to build the cpcc2_tiago package:

<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>colcon build --symlink-install --cmake-args '-DCMAKE_BUILD_TYPE=RELEASE'</code>
</pre>


You can also run the following command to use only one processor at a time, which will be less resource-intensive for your computer:

<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>MAKEFLAGS="-j 1" colcon build --packages-select <name_of_the_package> --cmake-args -DCMAKE_BUILD_TYPE=Debug </code>
</pre>


And then, after building, it is necessary to source the environement by using the command :


<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>. ~/TIAGO_perso/install/setup.bash </code>
</pre>


# Launching the simulation

To launch the simulation, open terminator and click on Ctrl + e to split the windows into to half. On one, run the command : 

<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>ros2 launch tiago_gazebo tiago_gazebo.launch.py is_public_sim:=True </code>
</pre>


And on the othern run 

<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>ros2 launch cpcc2_tiago cpcc2_tiago.launch.py</code>
</pre>



# Origin of repositories.

All packages, except for cpcc2_tiago, pinocchio, and crocoddyl, can be found on the Pal Robotics GitHub page.

You can find all the packages needed to run the TIAGO simulation on Pal Robotics' GitHub at the following address: https://github.com/orgs/pal-robotics/repositories?type=all

### Warning !

Be aware that if you use the Pal Robotics repositories directly, updates to your PC may affect the locally installed packages due to the frequent updates from Pal Robotics. Therefore, you will need to regularly update the software as follows:

#### How to Update Code from GitHub

To update your local code from a GitHub repository, follow these steps:

1. **Open Your Terminal:**
   Start by opening your terminal or command prompt. This is where you'll enter the commands to update your code.

2. **Navigate to Your Project Directory:**
   Use the `cd` command to change to the directory of your project. For example:
  
<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code> cd path/to/your/project</code>
</pre>

3. **Check the Remote Repositories:**
   To see which remote repositories are configured, use the command:

<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>git remote -v</code>
</pre>

4. **Check the Current Status:**
   Before pulling updates, it's a good idea to check the current status of your local repository:

<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>git status</code>
</pre>

5. **Pull Updates from GitHub:**
   To fetch and integrate changes from the remote repository, use the git pull command. If you're working with a specific branch, such as humble-devel, you would use:
<pre style="background-color: #f0f0f0; padding: 10px; border-radius: 4px;">
<code>git pull origin humble-devel:humble-devel</code>
</pre>

This command fetches the latest changes from the humble-devel branch on the remote repository (origin) and merges them into your local humble-devel branch.

   
