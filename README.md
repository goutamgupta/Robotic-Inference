# Robotic-Inference
Udacity Robotics Nanodegree Term II : Inference project
Start DIGITS
Start the DIGITS server by entering the command digits into a terminal. This will begin the boot of the DIGITS server (it will take a minute).

Now, from another terminal run print_connection.sh in order to get the link for the DIGITS GUI (Graphical User Interface). Keeping this script running will keep your workspace active if you are training a network but be sure to quit it if you are not using the workspace as it will use all of your GPU hours.

The Data
Let’s pause for a moment to talk about the data you will be training. There are three types of datasets : 
1. Udacity supplied dataset 
2. Data  collected from Webccam on Jetson TX2 EV kit for Indian Currency. 
3. Data collected from Webcam on Jetson Tx2 for various lab components. 

Once your data is imported, it is up to you to choose a training model. You can use a pre-supplied one, one from the DIGITS model store, an external network or even customize the above choices.We have chosen GoogleNEt for all the three mentioned applications. 

Your model will have to achieve an inference time of 10 ms or less on the workspace and have an accuracy greater than 75 percent.

Evaluate the model
Test your trained model by running the command evaluate in another terminal with the DIGITS server still running, but only after you are done training your model. It will ask you for the model’s job id which can be found from Digits workspace. It will then print out the results of this model. The evaluate command checks the inference speed of your model for a single input averaged over ten attempts for five runs. 

Collecting the images : camera_Nd.py script is used to collect the image from Jetson Ev kit. Note that opencv should be properly installed before using this script. Instrucution for installation of OpenCv can be found here: 
https://github.com/AastaNV/JEP/blob/master/script/install_opencv3.4.0_TX2.sh

Optional Deployment
Now that you have trained your network, ready to see it in action? Great - let’s get started!

The first step is to download your model from DIGITS to your Jetson. To do this, navigate in a browser on the Jetson device to your DIGITS server. From there download your model.

Next, create a folder on the system with a name for your model and extract the contents of your downloaded file into that folder with the tar -xzvf command.

Then, create an environment variable called NET to the location of the model path. Do this by entering something like export NET=/home/user/Desktop/my_model into the terminal. The exact command will depend on the shell you are using.

Navigate to the Jetson inference folder then into the executable binaries and launch imagenet or detect net like so:

./imagenet-camera --prototxt=$NET/deploy.prototxt --model=$NET/your_model_name.caffemodel --labels=$NET/labels.txt --input_blob=data --output_blob=softmax

You will then observe real time results from your Jetson camera!
