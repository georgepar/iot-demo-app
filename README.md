# iot-demo-app
A simple Internet of Things demo app I created for a project in Embedded Systems course in NTUA

The app was created using 2 Intel Galileo boards and a virtual server.
The backend (cloud app) was created using PHP and MySQL, and the Galileos gained access to it using Python (+ mechanize) and Bash scripts.

SETUP

server: 
    The files go in the /var/www/html directory of a lampp server (or something equivalent)

galileos:
    1. mount a Yocto image and install pip and mechanize:
            #wget --no-check-certificate https://bootstrap.pypa.io/get-pip.py
            #python get_pip.py
            #pip install mechanize
    2. burn the image in an sd card and boot the Galileo.
    3. echo "source setup.sh" >> .bashrc (different setup.sh for the sensor and the actuator)
    4. if "nohup" and "watch" commands are available run:
            #nohup watch -n60 "python {sensor,actuator}.py" 
       in the appropriate device else run 
            #sh run.sh
       so that the Galileos and the server update the shared data every 1 minute..
