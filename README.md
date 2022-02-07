# Lab 0 - Setup

This just makes sure you can run programs written in a variety of languages using my docker image. 

# Create your machine
First, [install docker](https://docs.docker.com/get-docker/) on your system.

Once docker desktop is installed, please modify the settings as follows:
- Go to Settings
- Go to Docker Engine
- Type the following code immediately after the first curly-brace:
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

# Start your machine
```
docker start -ai cse465
```

#  Create an environment variable for your user
```
export SID=<Your student id>
echo export SID=$SID >> ~/.bashrc
```

# Testing Your Code

In a terminal, type
```bash
docker start -ai cse465
git clone https://gitlab.csi.miamioh.edu/CSE465/$SID/lab0.git
cd lab0
timeout 5m make check
```


You should see "Success!" printed several times. 

# Submitting Your Results

Type 
```
timeout 5m make check && make submit
```
and paste the output into canvas.
