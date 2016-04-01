# Project: Poor Man's Alexa Voice Service

## About the Project
This is a fork of https://github.com/amzn/alexa-avs-raspberry-pi.
And modify to access and test the Alexa Voice Service using a Java client, and a Node.js server on a Ubuntu VM.
___

## Getting Started

### Hardware you need

1. Your normal PC

### Skills you need

1. Basic programming experience
2. Familiarity with shell

---

##  0 - Setting up the VM

This instruction assumes you know how to setup a Ubuntu virtual machine on your PC.

___

## 1 - Installing utilities & dependencies

### 1.1 - Install VLC

**MY NOTE:** Not entirely sure if this is really needed. Just follow the original instruction.

Get VLC media player by typing:

	sudo apt-get install vlc-nox vlc-data
	
**Make sure VLC is installed correctly**

	whereis vlc

This will tell you where VLC is installed.

**Set the environment variables for VLC**

Type the following into the terminal:

	export LD_LIBRARY_PATH=/usr/lib/vlc
	export VLC_PLUGIN_PATH=/usr/lib/vlc/plugins

**Check if the environment variables were set successfully** 

	echo $LD_LIBRARY_PATH
	> /usr/lib/vlc
	
	echo $VLC_PLUGIN_PATH
	> /usr/lib/vlc/plugins


### 1.2 Download and install Node.js

	sudo apt-get update 
	sudo apt-get upgrade

Set up the apt-get repo source:

	curl -sL https://deb.nodesource.com/setup | sudo bash -

Install Node itself:

	sudo apt-get install nodejs	

### 1.3 Install Java Development Kit

You need to have Java Development Kit (JDK) version 8 or higher installed. 

**Step 1: Download JDK**
Download JDK 8 from [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html). 

Download the tar.gz file listed correspond to your VM. Mine is **Linux x64** from the Oracle link above. At the time of this writing, the name of this file is jdk-8u77-linux-x64.tar.gz.

**Step 2: Extract the contents**
Extract the contents of the tarball to the /opt directory:

	sudo tar zxvf jdk-8u77-linux-x64.tar.gz -C /opt
	
Set default java and javac to the new installed jdk8.

	sudo update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_77/bin/javac 1
	
	sudo update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_77/bin/java 1

	sudo update-alternatives --config javac
	sudo update-alternatives --config java

**NOTE**: If asked to choose an alternative, type the number corresponding to the jdk version you just installed - for example - jdk1.8.0_77

Now verify the commands with the -version option:

	java -version
	javac -version

### 1.4 Install Maven

**Step 1: Download Maven** 

	sudo apt-get install maven

You can test that it is working with the following command:

	mvn -version

---

## 2 - Getting started with Alexa Voice Service

Follow all other instructions exactly as per the original project, but ignore the step about "Upgrade Your Java Version".