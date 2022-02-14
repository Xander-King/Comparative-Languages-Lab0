# Lab 0 - Setup

This just makes sure you can run programs written in a variety of languages.


You will do the following:
1. Ensure that you can have access to a linux environment with all of the necessary software.  
You may EITHER:
   - [Use CECLNX01](#instructions-for-linux), the university's linux server
   - OR [Use my Docker Machine](#instructions-for-docker) 

   And, **of course**, you will do the next steps in that linux machine. 
2. Save your student ID in an environment variable
      ```
      export SID=<Your student id>
      echo export SID=$SID >> ~/.bashrc
      ```
      This way I can use $SID in place of your student ID whenever I give instructions in the future. 
3. Set up SSH access to gitlab  
     Follow the instructions on https://gitlab.csi.miamioh.edu/-/profile/keys  
     This typically amounts to typing
      ```
      ssh-keygen
      ```
      then
      ```
      cat ~/.ssh/id_rsa.pub
      ```
      and then copy & pasting the key into the URL above.  



4. Test Your Code

   In your linux terminal, type
   ```bash
   git clone git@gitlab.csi.miamioh.edu:cse465/$SID/lab0.git
   cd lab0
   make check
   ```
   You should see "Success!" printed several times. 

5. Submit your Results

   Type 
   ```
   make submit
   ```
   **Of course** if you see an error message, then your submission did not succeed!


   **You do NOT need to submit anythin on canvas**, however pasting the result of running `make submit` can help us to diagnose any unusual issues you may have had in your submission.



# Instructions for CENLX01
 This is the simplest option, however you are not an admin and cannot install software on our server. This option also does not support remote access using VSCode.  
 You all have access to CECLNX01.  
 To use it,  open up a terminal (e.g. a command prompt, or PUTTY, etc.) and use SSH to connect to `ceclnx01.csi.miamioh.edu`.  For example, on my system I type:
 ```cmd
 ssh femianjc@ceclnx01.csi.miamioh.edu
 ```
 where `femianjc` is my username. 
 Use your university password and accept any certificates etc. to access CECLNX01. 

 I reccomend you create a folder for this course
 ```
 mkdir -p ~/cse465
 cd ~/cse465
 ```
and put all coursework in one place. 


# Instructions For Docker
**Docker is NOT required**, but it is a useful way to make sure you can edit and run programs for this class. 

Specifically, docker works will with [VSCode](https://code.visualstudio.com/),  which will help you to be more productive and spend less time on your assignments, at least in theory. 

First, [install docker](https://docs.docker.com/get-docker/) on your system.

Unfortunately, Miami Univerisite's IT team is using the range of IP addresses needed by docker for something else.  To work around this you need to change a configuration setting in docker.  
Once docker desktop is installed, please modify the settings as follows:
1. Go to Settings
2. Go to Docker Engine
3. Type the following code immediately after the first curly-brace:
   ```
   "default-address-pools":  [    {"base":"10.10.0.0/16","size":24}  ],
   ```
   do not forget to preserve the comma and make sure you include all the quotes etc.   
   This setting is to work around Miami IT's IP address range limitations. 

From _your_ host computer:
```
docker create -it --name cse465 jfemiani/cse465
```
NOTE: This is one time that you exactly copy the id "femianjc" and do not replace it with yours. This is the name of may account on dockerhub, where I have uploaded a machine for you all to use.  

### Start your machine
```
docker start -ai cse465
```


