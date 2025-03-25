1. boot up raspberry pi

2. set up wifi/ethernet

3. system update commands
```shell
	sudo apt update
	sudo apt upgrade 
```

4. setup and activate virtual environment named audio for the experiment (to avoid conflicts in libraries) as below:
```shell
	sudo apt install python3-venv
	python3 -m venv audio
	source audio/bin/activate
```

5. connect and test microphone 
	- physically connect microphone to the pi
	- test the microphone ([[How and what command do you use to test the microphone?]])


---
After setup, we can now move to testing our microphone. Go to:
[[Part 2 - Test the microphone]]