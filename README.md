# Coachbot Swarm User Guide

Written and Maintained by Vaishnavi Dornadula (vaishnavidornadula2026@u.northwestern.edu)  
Last Updated: August 20th, 2024

We ask that you respect the system and help us keep it accessible to fellow academics by adhering to the guidelines explained in this guide. We reserve the right to refuse access to any individuals who are not courteous to the system or the Coachbot team.
If you have any questions, comments or concerns, please email us at coachbotswarmsystem@gmail.com and someone from our team will get back to you.

## Overview of System

### How Does the Swarm Function

#### Arena
![Arena and Play Area](https://github.com/dornadulavaishnavi/coachbotuserguide.github.io/assets/90789243/22bbe2c1-af4e-432a-ae49-c05bfe4c342a)

The arena is shown above with the axis labeled and the play field highlighted. The play field runs from -1.2 to 1.0 meters in the x and -1.4 to 2.35 meters in the y. The arena houses charging rails for the robots along two of its walls and the swarm will automatically charge between submissions if more than half the swarm is approaching a low voltage. 

#### Coachbots

The coachbot robots communicate with each other over a server and can do all-to-all communication. If you wish to restrict the communication radius, you must manually do that in your algorithm. A common way to do this is to send location along with the message so each robot can calculate its distance to the robot sending the message and discard it if it is outside the desired communication radius. For more information on sending messages, please refer to sections below about the available robot API and communication. These purple, cylindrical robots have unique IDs which will be mapped to the positions specified by the user in one of their submission files detailed below. Each robot is around 11cm in diameter and is 14cm tall.

### Getting Started with Git
For our testbed, we currently use the popular system, Github, as a platform for users to submit their experiments to and receive results. To get started, make an account on https://github.com/ (a free account will be sufficient for our system). There are two popular ways to use Github on your local machine, which are explained below. Our Github organization, Coachbot-Swarm, houses the repositories for experiment submission and example code as well as private user repositories. ***https://github.com/Coachbot-Swarm***

#### Github Desktop

Github Desktop is a convenient interface to utilize git tools without needing to use the terminal. Download the tool from https://desktop.github.com/. Look for the “Current Repository” Menu on the top left below the banner. In that dropdown menu, click “add” and select “Clone repository…”.  In the Github repo linked above, select the green “< > Code” dropdown button and copy either the https or ssh link. Which you choose is a matter of personal preference, but here is a reference to learn more about the differences: https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories. Once you have either the https or ssh link copied, go to Github Desktop and paste this link in the “URL” section. Make sure your local path points to where you want the repo to be housed and click the blue “clone” button. Now you should be able to pull by clicking “Pull Origin” in the top banner, see your changes on the left bar, commit changes in the bottom left corner, and push code with the button in the top banner. The option to push will not appear if you have no changes. Please remember to always pull before you push and save a local copy of your code outside the repo.  

#### Terminal

To use git through your preferred terminal, you must first download the appropriate packages. Follow this link to download Git for your OS: https://github.com/git-guides/install-git. Once you have downloaded git and checked for successful installation, you can close the repo. In the Github repo linked above, select the green “< > Code” dropdown button and copy either the https or ssh link. Which you choose is a matter of personal preference, but here is a reference to learn more about the differences: https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories.  In your terminal, navigate to where you want the local repo to be housed. Type *git clone* and paste the https or ssh link and hit enter. This will clone the repo to your local folder and you can now create your folder in the code queue. *git status* will tell you if there are any changes on your local system that have not been sent to the repo. As a good git practice, please remember to always run the git pull command before you git push to avoid any conflicting code between collaborators. A quick guide to important and commonly used git commands can be found here: https://training.github.com/downloads/github-git-cheat-sheet/. The commands that will most commonly be used are *git pull, git status, git add, git commit,* and *git push*.

#### Note for Chromebook Users
Github is not inherently supported on Chromebooks and thus will require some extra setup. We recommend following these two guides to get git set up either for terminal or Github Desktop usage.

GitHub Desktop Setup Guide: https://www.addictivetips.com/chromebook/install-github-desktop-on-chrome-os/

Git Terminal Guide: https://www.geeksforgeeks.org/how-to-install-git-on-chrome-os/

#### Requesting Access to the Organization

To gain access to our Coachbot-Swarm organization and start submitting experiments, email us at coachbotswarmsystem@gmail.com with your name, university (if applicable), and github username associated with the account. You can find your github username by clicking on your profile picture in the top right corner and going to “Your Profile”. Your username will be underneath your large profile picture icon on the left side. After emailing us, users will receive an email (to the address linked to the Github username) inviting them to join the Coachbot-Swarm organization. Please allow up to one business day for this invitation from when we were emailed. Once the user accepts the invite to the organization, they'll get write access to two repositories. The first of the repositories is named *submission_repo*, where users will be able to, as the name suggests, submit experiments. Details on this process are outlined in sections below. The second is a private repository which has the same name as the Github username that was requested to be a collaborator to the platform. This repository is where the user and any collaborators they choose to add can iterate on experiments, prep files for submission, and access results. This private repository contains a skeleton template for the 4 files explained below that a submission is comprised of. Further sections below walk through the files needed for submission and the available robot API functions. If you already have git installed on your machine, continue on to steps below for getting starting with your first submission. If not, please refer to the previous section about git installation.

## Getting Familiar with the System through the Example Repository
The third repository seen in the organization is *Examples*. This repository contains various examples of submissions highlighting different robot API calls and is a great starting reference point to get familiar with how to submit to the Coachbot Swarm Platform. The simple steps below will help users submit their first experiment to the platform.
1. Clone the Example repository to your local system
2. Navigate to the "Simple Example" Folder and view the 4 files present which make up a submission
3. Clone your private repository to your local system (this will be the repository named with your github username that you received access to once you accepted the invitation to join the Coachbot-Swarm organization)
4. Copy these 4 files to your private repository (without the folder)
5. Open the email_simple_example.txt file and enter in the email address you would like to be associated with this submission
6. Change the name of the github_username.json file to be the github username that matches the name of your private repository (ex. if my github username/repo name is dornadulavaishnavi, then my new file would be dornadulavaishnavi.json)
7. Push these 3 experiment files to the main branch of the private repository. (*usr_code.py*, *init_pose.py*, *email.txt* or the alternative name you've given it)
8. Clone the *submission_repo* repository to your local system
9. Copy just your renamed .json file to the *submission_repo* and push to the main branch
10. Your example code has now been submitted to run on the Coachbot Swarm Testbed (Note: when the testbed is running, the submission is immediately loaded locally and deleted from the repository)
11. Users can expect to receive up to 3 emails from the system per submission, one confirming validity, one for the start of the experiment, and the last being a notification of completion.
12. The results of the experiment will be found on a new branch in the user's private repository with the appropriate time stamp.

To begin experimenting with the platform, we recommend taking a look at these files and editing them to create your first submission. Try changing the initial positions and number of robots in the **init_pose.csv** file or edit parameters to change behaviors such as how long the robots drive for or their LED color to understand how the API calls work.
 
## Submitting your Code

Every submission to our system consists of 4 components. The first is a file that you will push to the *submission_repo* when you are ready to run your experiment on the physical testbed. This file is of type .json, referred to in this guide as **submission_repo.json**, and points to where and under what name to find the required input files (detailed below) in the main branch of your private repository. These 3 required input files are the code that the active robots will run, initial positions the robots should be in at the start of the experiment, and lastly, an email to be notified about experiment progress. The code that will be uploaded to all active robots, referred to here on out as **usr_code.py**, must be written in python (robots currently run python 2.7.16) and formatted in the way outlined in sections below. The second file, referred to as **init_pose.csv** specifies the initial positions of the robots before the user code is run. Lastly, we have a text file, referred to as **email.txt** which simply contains the email address that should be contacted about that experiment. Remember to make sure the name of these three files match the ones you right in the **submission_repo.json** file. 

After pushing these 3 completed, required files into the main branch of the user's private repositoy, make sure to fill out the *github_username.json* with the appropriate files names and rename this .json file to the github username of the private repository. The 3 required input files described in the paragraph above are not required to be name the same as the terms we use in this guide but they do need to be the same file types and the name must be specified in the .son file.  This .json file then needs to be copied and pushed to the submission_repo repository to be submitted to our platform and run on the Coachbot robots. See the Github section above for a refresher on how to contribute code to a repository. Once the .json has been pushed to the submission_repo repository, the experiment has been successfully submitted to the testbed!

Another simple way to submit your code on the submission Github repository is to directly create the file on the github website. Navigate to the submission repository home page and find the button on the right that says, 'Add file'. Click on that button and select the 'Create New File' option from the drop down menu. Here, you can name your file *your_github_username.json* with your personal username and fill in the contents as shown in the example file in the private repository or as shown below with the default file names.

{

&emsp; "usercode": "usr_code.py",

&emsp; "initialpositions": "init_pose.csv",

&emsp; "email": "email.txt"

}



A skeleton example of all 4 of these components are given in your private repository and other examples are included in the Example repository of the organization.

### Input Files

#### User Code

The user code file, **usr_code.py**, needs to be written in python. This same code will be uploaded to every active robot that will run your code. The section below explains the available robot functions and various functionality such as sending messages and logging. Instead of a main function, the robot code will look for a function called *def usr(robot):* so be sure to add that to your code as shown below. It is also good practice to add a small delay in the while loop (See example code for reference).

**usr_code.py** format:

*imports  
def usr(robot):  
&emsp; # write code here  
&emsp; &emsp; while condition:  
&emsp; &emsp; &emsp; robot.delay() # defaults to 20 ms which is sufficient  
&emsp; &emsp; &emsp; # more code here  
return condition*  

The current time limit for code runtime is 10 minutes so if your code hits this limit, it will pause the code and return all the information it received until that point.

#### Initial Positions

The initial positions of each robot must be specified in a csv file, refered to as **init_pose.csv**. The values specified must follow the rules listed below. The x and y positions are in meters while the theta value is in radians (-2π, 2π). The arena orientation and sizing is further specified above. 
- Each row should specify an ID number, x position, y position, and theta angle in radians. The ID number should be a whole number integer, while the x, y, and theta positions can be floats.
- The play field is sized at -1.2m to 1.0m in x and -1.4m to 2.35m in y so the x and y positions must be within those dimensions. 
- There are currently 50 robots active in the Coachbot swarm so please limit your number of robots to 50.
- The ID number must be between 0 and 49.
- Each robot must start at least 25 cm away from each other.
- The x and y positions are in meters while the theta value is in radians (-2π, 2π) 

Example **init_pose.csv** file:

0,0.75,1.0,3.14  
1,0.5,0.5,1  
2,-0.5,-0.5,0  
3,-0.1,-0.1,1  
4,-1,-1,0  
5,-0.5,0.5,1  
6,0.5,-0.5,1  
7,0.25,0.25,3.14  
8,-0.25,0.8,2.5  
9,0.75,-0.1,1.5

If your **init_pose.csv** file does not abide by the rules above, you will receive an email and can check the **input_pose_errors.csv** file for details on where it failed. 

#### Email

The **email.txt** file should simply contain the email address all alerts should be sent to. Users will receive an email notification when their code begins to run and one when it has completed. The user may also instead receive an email letting them know that their initial positions were invalid or their code hit the time limit.

### GitHub Interface to the Coachbot System

When you accept the invitation to the Github organization, you will be able to view 3 repositories: submission_repo, Example, and one named with your github username. The submission_repo, discussed above, 
https://github.com/Coachbot-Swarm/submission_repo, is where users can upload their submission file to be run on the Coachbot Swarm Testbed. While the system is active, the submission is immediately loaded locally and removed from the repository. Details for the contents of this submission file (**github_username.json**) are explained above and examples can be found in the private user or Example repository. The Example repository contains various sample code of the four components of a submission highlighting different robot API calls and is a great starting reference point to get familiar with how to submit to or write algorithms for the Coachbot Swarm Platform. The last repository is the user's private repository whose name will match the user's github username. This repository is not visible to any other users of the Coachbot platform and users can add other collaborators to their repository that they wish. Users can iteratively build their code using the version control nature of github or simply upload code to their repository when they have finished developing. The algorithm user code, initial positions, and email files must be located in the main branch of the repository. Ensure that the name of these three files are specified correctly in the submission file which is pushed to the submission repo. Users will receive up to three emails per experiment submitted to the corresponding email specified in the submission. This will notify users for if their input files were valid, when their experiment has begun, and when their results have been returned. The results of your experiment can be found in your private repository in a new branch. This branch will be named with the timestamp of when the experiment ended.

## Writing Code for the Coachbots

Check out our API Overview tutorial here for a quick introduction:

[![](https://markdown-videos-api.jorgenkh.no/youtube/Z8qkd0gtyGM)](https://youtu.be/Z8qkd0gtyGM)

### Available Robot Functions

#### robot.set_vel(left,right)

Parameters: left and right should be whole numbers between -50 and 50 that indicate wheel speeds corresponding to the respective wheel. 0 being no movement and 50 being the fastest possible speed. The negative values indicate that the wheel would spin backwards at that speed. This function sets the speed for 1 second before stopping. These values have no unit.  

Output: none  

Example: *robot.set_vel(30,-40)*

#### robot.set_led(r,g,b)

Parameters: r,g,b should be integers between and 0 and 100 to set the color and brightness of the onboard LED  

Output: none  

Example: *robot.set_led(30,100,0)*

#### robot.virtual_id()

Parameters: none  

Output: An integer that is the virtual ID of the robot.   

Example: *virt_id = robot.virtual_id()*

#### robot.get_clock()

Parameters: none  

Output: a float of the number of seconds elapsed since the program started  

Example: *curr_time = robot.get_clock()*

#### robot.send_msg(msg)

More information about this send function and the receive function are explained in the section below.

Parameters: msg should be a string that is less than 64 bytes or it will be truncated. This msg can be the output of the struct.pack() function explained in the section below.  

Output: True is successful, False if not  

Example: *robot.send_msg(struct.pack(‘fffii’, float_0, float_1, float_2, int_0, int_1))*

#### robot.recv_msg()

Parameters: none

Output: Returns the messages in the buffer since the last call of this function.   

Example: *msgs = robot.recv_msg()*

#### robot.get_pose()

Parameters: none  

Output: a list with the [x,y,theta], check to see that this output is valid before using it or None if no position has been updated for the robot

Example: *pose = robot.get_pose()*

#### robot.delay()

Parameters: an integer value in milliseconds, default is 20ms but a different integer parameter can be specified  

Output: none  

Example: *robot.delay(500)*

### Sending and Receiving Messages

Sending and receiving messages is done through the *robot.send_msg()* and *robot.recv_msg()* functions explained above. The messages that these functions handle are created and read using *struct.pack()* and *struct.unpack()* so be sure to import struct at the top of your file if you plan to use messaging. For best results, add in a short (50ms) delay between any send and receive function calls. Example usage of these functions are shown below.

*struct.pack()* example:  
*struct.pack(‘fffii’, float_0, float_1, float_2, int_0, int_1)*

The first argument in the example above, ‘fffii’, specifies the type of variables being sent in what order and quantity. In this example, I am sending three floats and two signed integers. The remaining parameters are the corresponding variables I am sending in the message.

This line would be called in the following way, where the struct_pack() function is called and passed into the send_msg() function: robot.send_msg(struct.pack(‘fffii’, float_0, float_1, float_2, int_0, int_1))

*struct.unpack()* example:  
*struct.unpack(‘fffii’, msg_received[0][:24])*

The first argument, ‘fffii’ specifies the expected message content types. The second parameter specifies the variable I am reading from. Whatever variable I save the output of the *robot.recv_msg()* in will contain the entire buffer of messages. In this example, I am reading in the first message in the buffer and the [:24] specifies the message length, which is the byte length of the expected message. Since floats and integers are both four bytes each, we determine this message length by multiplying the number of variables expected in the message with the size of each variable, therefore, 6 x 4 = 24..

This function would be called in the following way, where the struct_unpack() function is called after receiving a message:

msgs = robot.recv_msg()

struct.unpack('ffi', msg[0][:12])

### Logging from the Robots

Logging is a very useful debugging tool, especially in a swarm, where many robots are running the same code. To log messages from each robot, we write to a file instead of using print statements. These individual log files will be available to you after your code is run as explained in the section below. In the **usr_code.py** file, add the following line of code to open the log file to write, *log = open(“experiment_log”, “wb”)*. The variable name of *log* can be different but the file being opened must be called *experiment_log* and it must be opened in binary write mode as indicated by the *wb*. To write to this file, use the write function with a string as the parameter *(log.write(string))*. Be sure to include the new line character *(\n)* at the end of your string so that each of your statements are on a new line. After every write, call the flush function *(log.flush())*. Be sure to close the file before your script returns *(log.close())*. 

## Getting the Results

When your code has finished running, you will receive an email from the system letting you know. View your private repository (named with the registered user's github repository) to access the results. The returned files will be in a new branch named with the timestamp of when the experiment finished. To switch branches, click on the dropdown menu, defaults to "main", near the top left of the screen, below the repository name to view the full list of available branches.

### Result Format

Assuming the submission was valid and passed our verification, users will receive an email alerting them that their experiment's results are ready. The code that ran in the system will be named the default submission file names, usr_code.py, init_pose.csv, and email.txt. The results of the algorithm will be pushed to a seperate branch in the private repo. This branch will be named with the time stamp of when the results were uploaded to the private repository. This branch will roughly resemble the following directory tree (new files and directories are in bold).

&emsp; FolderName  
&emsp; &emsp; usr_code.py  
&emsp; &emsp; init_pose.csv  
&emsp; &emsp; email.txt  
&emsp; &emsp; <ins> init_pose_errors.csv </ins>
&emsp; &emsp; <ins> sim_data.txt.csv </ins>
&emsp; &emsp; <ins> sim_output.mp4 </ins>
&emsp; &emsp; <ins> output_logs </ins>  
&emsp; &emsp; &emsp; <ins> ID_mapping.csv </ins>  
&emsp; &emsp; &emsp; <ins> camera_video.mp4 </ins>  
&emsp; &emsp; <ins> #_logging.csv </ins>  
&emsp; &emsp; <ins> # </ins>  
&emsp; &emsp; <ins> automation_errors </ins>  

The **init_pose_errors.csv** will contain the contents of **init_pose.csv** or list any issues with the initial poses specified. The output_logs folder will hold all the outputs from the algorithm run. Since the ID you specify in the **init_pose.csv** file might not match the physical robot ID, the **ID_mapping.csv** file specifies which robot corresponds to which virtual ID. The .mp4 file is the recording of the run from our overhead raspberry pi camera. The logging files (**#_logging**) will be named with the virtual ID of the robot it pertains to and contain the position of the corresponding robot at every timestep of the run. This csv file is formatted in a timestep, x position, y position, theta angle in radians for each line. The # file is the virtual ID of the pertaining robot and will have any information you choose to write to the **experiment_log** file in your code. The **automation_errors** file will list any high level errors such as runtime limits or robots trying to exit the play field.

### Automation Error Messages:

The **automation_errors** file will contain information of high level errors such as hitting the runtime limit or robots leaving the playfield. This will not have any errors your user code may hit so please be sure to use the logging features to assist with debugging. 

<ins> Runtime limit</ins>: If you receive an email saying that your code hit the time limit, please make sure your code hits its return conditions properly or reduce the runtime of your code. You will still receive all the information above for the length of time your algorithm ran and access it in the same way.

<ins> Robot out of Bounds</ins>: If you receive an email or see in your **automation_errors** file that some robots went out of bounds, please make sure that your code keeps the robots within the playfield. The message in the file should specify the offending robot and the position it left the field to help with debugging. You will still receive all the information above for the length of time your algorithm ran and access it in the same way.

### Other Troubleshooting

<ins> Git Merge Conflict</ins>: If you see this error on your local computer when you attempt to push your code folder, first make sure you have a copy of this folder and its contents somewhere on your local computer outside of the repo. If you encounter a git merge error, please do not override anything at the Head. This simply means that your local repo is not up to date with the remote repo and what you are trying to push directly affects these differences. The easiest way is to keep the changes at the Head and check that what you’re uploading has a different name than any of the newly pulled folders. (Ex. if someone uploaded a folder named swarm_test which happens to be the folder name you were using, change your folder name and that should resolve the conflict)

<ins> No Push Access</ins>: Make sure you go through the steps listed in the section about obtaining access to the Coachbot-Swarm organization and have received access to the system.

If you run into any issues or have any questions, please don’t hesitate to email us at coachbotswarmsystem@gmail.com.

## Acessing and Running Experiments on the Coachbot Swarm Simulator
Our testbed features a corresponding simulator that is compatible with Windows, Mac, and Linux machines. This tool is publicly located through Github and can be used to test algorithms at faster speeds and larger swarm sizes before being run on the physical testbed (***https://github.com/michelleezhang/swarm_simulation/tree/master***). Exact instructions on using this simulator are located in the README of its repository. Once the results on the simulator match the expectations of the user, it is then ready to be run on the physical testbed.

## Changing the Code to Run on the Physical Coachbot Swarm System
To effectively change the code of the algorithm from running on the simulator to the physical testbed, a few function names currently need to be changed. The physical robots use the function robot.virtual_id() to access their ID numbers instead of the simulator's equivalent function, robot.id. Similarly, instead of print statements used in the simulator, the physical testbed can track these statements through the user writing these statements in a log.write() as shown in the example *usr_code.py*.

## Coachbot FAQ

**Q**: The CoachbotSwarm Github repository says I do not have push access, how do I fix that?  
**A**: If you are unable to push to the repository, please make sure you have been granted contributor access. Email coachbotswarmsystem@gmail.com with your name, university (if applicable), and github username/email address you will be notified 

**Q**: I submitted my experiment but I no longer see it on the repository queue and did not receive any emails regarding the status of my experiment. Is there something wrong with the submission?  
**A**: There could be a few reasons why there were no alerts about the experiment.  Double check your spam folder to ensure that any experiment alerts have not accidentally ended up there.
The first most common reason would be that the swarm is currently charging and not running any experiments. In this case, the experiment is still queued up locally even if it is no longer on the repository’s queue. 
The second reason could be that the system could not find an **email.txt** file to send notifications to. If  this is the case, it will still attempt to run the experiment and you can find your results in the **Completed_Runs** folder of the repository in a folder with the same name as your submission.

**Q**: If I don’t care how many robots are used in my experiment or where they start, do I still need to submit an initial positions file?  
**A**: Yes, you will still need to submit an **init_pose.csv** file in your experiment for it to be run. Feel free to use the files provided in the **Example Folder** and edit as needed.

**Q**: I uploaded my submission (.json file) to the submission_repo and no longer see it. I also have not received an email from the testbed confirming that my input files are valid. Did my submission go through correctly?
**A**: If you no longer see your submission in the submission repo, that means that the testbed was active and locally loaded your file. Please ensure that the .json file submitted's name matches that of the private user github repository where the algorithm can be found. Also double check the the file names listed in the .json file match those of the files in the main branch of the user's private repository.
