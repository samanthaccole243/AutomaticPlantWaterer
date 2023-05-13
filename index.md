### Do you love plants, but always have them end up looking like this? 


<img width="299" alt="image" src="https://user-images.githubusercontent.com/89661904/236704407-b3c708fd-3550-4f1b-8e71-5645bf7ebfcb.png"> <img width="530" alt="image" src="https://user-images.githubusercontent.com/89661904/236704478-69dfd48c-00a6-4b79-8df5-cdbd6248e2e8.png">

!Warning!
This Project will solve all your plant problems! 

# Automatic Waterer
   
## Project Introduction

This project focuses on building a system that waters your plants for you with little to no effort. Just set it up, and refill the water tank when your told and you will have beautiful happy plants! 



<img width="297" alt="image" src="https://user-images.githubusercontent.com/89661904/236705943-0a679097-da5c-462c-af3a-b335baf13629.png">


## High level Overview

### Setup:
The base model of this kit comes with a black soil moisture sensor (leftmost), a red water level sensor (mid-left), a temperature and humidity sensor (middle), a water pump with tubing (mid-right) and a raspberry pi along with all the associated circuitry and two power chords (rightmost).


__Picture__

The temperature and humidity sensor just needs to be left in the open near the plants so it can assess the air conditions.
The black soil moisture sensor should be placed in the soil of a plant as seen here:

__picture___

The water pump with tubing attached and the red water level sensor should be placed in your water source as seen here:

__picture___


The other end of the tubing should then lead to the soil of your plant. The raspberry pi needs to be connected to a power chord. A matching power chord also needs to be plugged into the residual female usb-c. This is used to power the water pump. Originally in the lab, a 5v power supply was used, but using a power chord with no additional hardware plugged into the wall, will also provide a 5V power supply, so we chose to incorporate this so anyone could set this up in their own home.

Here is a picture of the setup with an actual plant:

___picture___

For our demo purposes within the video, you will see us use two clear plastic cups. One represents the water source (cup containing red sensor), while the other represents the soil (cup containing black soil). We utilize these clear cups for testing and demonstration since it is easier to see what is physically taking place. It is also easier to reset the work bench after running the system by simply emptying the black cup.v This is much faster than waiting for the soil to dry back out.

### Screen displays and overall functioning:

Now we can examine what happens on the raspberry pi for the automatic plant waterer to function. After pluggin in the raspberry pi, it should turn on. Run the program, as seen in the video by typing ___________________help___. Then you will see a screen with a plant name, a select button and some arrows. The screen will look something like this:

___picture____

Using the arrows, navigate through the different plant options, and choose the plant you are trying to water automatically. If your plant is not there, no problem. You can either watch our video for more details on how to handle this or scroll down to the "What to do if you plamt is not in the initial list" section, then return here when finished.

Once you have found the screen with your desired plant, click select. A screen similar to the image below should appear.

__picture___

This screen displays the air moisture and temperature as measured by the humidity and temperature sensor. Unforutnately for the current model, we were not able to actually get this sensor working appropriately. We will discuss this more in the "Challenges" section. Therefore, the screen simply displays room temperature and 50% percent humidity for now. Next the soil moisture sensor reading can be seen. This number will change slightl as the sensor will contain a bit of noise. The number will also increase drastically after watering, since the soil will be much more moist. The next line confirms that the water level is okay. Then the threshold for the particular plant is displayed. The user has the option to either increase or decrease the threshold according to their will. Just remember that the threshold originally set for that plant is recommended and any changes might starve or drown your plant. We do recognize however that some plants vary and you might want to be able to control the threshold yourself. 

Staying on this screen will make sure that you plant is automatically watered to its preferred threshold, as long as your water source remains filled. You will know your plant is actively being whatered when you see this green progress bar, seen below, scanning across the screen; and you will probably hear the pump. 

__picture__

When the water source is empty the user will have to refill it. If the water pump were to run out of water to pump and try to pump air and water, it may be damaged or break. Luckily, our program watches out for this situation. If the water level sensor senses that the water level is low. The raspberry pi screen will flash a red "water tank empty" warning as seen here:

__picture___

It will also not water your plant even if the plant is dry, since there is no water to pull from in the water source.

Now what happens when eventually you want to move the system to another plant? Simply click the bottom right physical button on the piTFT to quit the program. A new screen (seen below) will appear asking if you want to report? yes or no. 
___picture___
If the plant has sadly passed on, we ask that you click that yes button, so we know which settings killed your particular plant type. This helps us guide users in the future to keep them from making the same mistake. IF you siply want to power down the program or switch from one type of living plant to another, then click the "no" response and the program will be ended.

### FAQS: 

### What should you do if you plant was not in the list?
If the person ordering our product is skilled with github, they may provide us with a github repository. Our pi currently pulls a text file from our git repository every time the code is run, to determine which plants and asssociated thresholds to display. We can set the pi up to pull a specific text file from your repository instead. For this to work seemlessly, there must be no mistakes within how the repository or text file is named and what the pi is told to pull from. The text file also needs to be in the exact format where each line contains a plant name , plant threshold. The text file must look something like this:

___picture___

The threshold can be found by simply googling the web and finding out what soil moisture level (percentage number out of 100) the plant prefers.

If someone is not so familiar with github, no problem! They can simply email our manager with a new plant type to add, and he will handle the rest! The new plant type along with its recommended threshold will 'magically' appear on your pi soon after our manager reads his email!

### How do the reports work?
Once a plant death is reported, a file will be pushed to our (the project managers') github. This file will be named with the date of the report and contain the plant type and threshold the plant was set to before it died. We can then carefully compile this data and observe any common trends between plant types.

### Can this be customized with different sensors?
Absolutely! Scroll down to the "Future Uses" section for more details!

## Design and Testing:

### Testing
The testing portion of this project mainly consisted of low level circuit debuggin (using hardware debugging methods) and running our code while hoping it worked. When it didn't, we would examin the error and try to rectify the issue the error was pointing to. We will discuss particular challenges, often highlighted by these tests in the "challenges" section. 

### Design
There are two main design areas to discuss: Hardware and Software.

### Software
The main design considerations for the softare consisted of deciding how the screen should look and how the code should run. Certain software elements were decided directly by the hardware, like which ports to set up or when to enable which things. Most other things could be chosen by us, the project creators. 


After much discussion, we came up with a way we wanted everything to run. We would have a bash script (pictured underneath) with lines, commands, and  programs which would run sequentially. To be clear this means no program is running in the background. 

<img width="696" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/3ee2c916-8743-4be6-8d7d-ef1feacda9e0">

The whole structure of the automatic watering machine bash file code can be simplified into the following steps:

1. Git pull: pulling the whole repository from GitHub to avoid push problems later.

2. Git02.py: downloading the plant_threshold.txt as plant_thresholds.txt 

3. Readtxt02.py: read the plant_thresholds.txt downloaded from github and show plant choices on the screen for users to pick. The selection will be saved into file ‘new_plant_threshold.txt’

4. Test007_3.py: the main code for watering logic. It reads the previous ‘‘new_plant_threshold.txt’ as default thresholds and allows users to change it dynamically. It will save the plant name and threshold used at the end of the program into ‘bad_plant_threshold.txt’ at the time it’s terminated by the quit button.

5. Report02.py: give user a choice to report bad threshold on their plants. If choose ‘yes’, a new txt file named ‘report_2023-05-10_19-45-06.txt’(for example. The date and time will be the exact time) will be pushed to GitHub Repository.

Next we will go into detail regarding each step, why we made this design choice, and display proof of its functioning.

Step 1: Git pull
This step is important, because we need the local GitHub repository to be up-to-date, otherwise it will refuse the git push later. To pull the repository, we need to enter that folder first, then run this ‘git pull’ command. This is why you see this step written like so: 

<img width="463" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/ecaacca3-0c85-4661-aeda-93a041ba27b5">

While running the terminal will display something similar to this:

<img width="380" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/68a410c8-681c-4997-916b-021610637cb0">

This results from pulling a file which is already up to date on the system. If somehting within the repository had been changed the pull would look slightly different.

This step is an important starting place, because we now have access to any updates if a new plant has been added to the text file. Also Later in our program we allow users the option to push to the repository. If this took place without first initially pulling and just pushing from the raspberry pi, if a file was changed on the github end and it was not reflected on the pi, the push might overwrite the change that was made on the github end as if it never happened. 

We realized this was an important first step since luckily github warns you if you are going to push to a repository before pulling any possible changes. We were able to catch this and implement a fix so no overwrites take place!


Step2: Git02.py: downloading the plant_threshold.txt
Here is a look inside the Git02.py file:





