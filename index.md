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
The base model of this kit comes with a black soil moisture sensor (leftmost), a red water level sensor (mid-left), a temperature and humidity sensor (middle), a raspberry pi along with all the associated circuitry and two power chords (mid-right), and a water pump with tubing (rightmost).


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

<img width="327" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/dd4f01a7-5098-409d-aa39-b8adecc56ef2">

Using the arrows, navigate through the different plant options, and choose the plant you are trying to water automatically. If your plant is not there, no problem. You can either watch our video for more details on how to handle this or scroll down to the "What to do if you plamt is not in the initial list" section, then return here when finished.

Once you have found the screen with your desired plant, click select. A screen similar to the image below should appear.

<img width="239" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/54f1ebc6-72a6-4504-9f92-b5622ec6c419">

This screen displays the air moisture and temperature as measured by the humidity and temperature sensor. Unforutnately for the current model, we were not able to actually get this sensor working appropriately. We will discuss this more in the "Challenges" section. Therefore, the screen simply displays room temperature and 50% percent humidity for now. Next the soil moisture sensor reading can be seen. This number will change slightl as the sensor will contain a bit of noise. The number will also increase drastically after watering, since the soil will be much more moist. The next line confirms that the water level is okay. Then the threshold for the particular plant is displayed. The user has the option to either increase or decrease the threshold according to their will. Just remember that the threshold originally set for that plant is recommended and any changes might starve or drown your plant. We do recognize however that some plants vary and you might want to be able to control the threshold yourself. 

Staying on this screen will make sure that you plant is automatically watered to its preferred threshold, as long as your water source remains filled. You will know your plant is actively being whatered when you see this green progress bar, seen below, scanning across the screen; and you will probably hear the pump. 

<img width="236" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/92946689-da88-4da7-8949-dcd55560b047">

When the water source is empty the user will have to refill it. If the water pump were to run out of water to pump and try to pump air and water, it may be damaged or break. Luckily, our program watches out for this situation. If the water level sensor senses that the water level is low. The raspberry pi screen will flash a red "water tank empty" warning as seen here:

<img width="241" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/a24a5a03-abe5-47a7-8aa3-265da47ed59f">

It will also not water your plant even if the plant is dry, since there is no water to pull from in the water source.

Now what happens when eventually you want to move the system to another plant? Simply click the bottom right physical button on the piTFT to quit the program. A new screen (seen below) will appear asking if you want to report? yes or no. 

<img width="209" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/f4259481-2fc6-4009-b5c6-2d59bfdb267e">

If the plant has sadly passed on, we ask that you click that yes button, so we know which settings killed your particular plant type. This helps us guide users in the future to keep them from making the same mistake. IF you siply want to power down the program or switch from one type of living plant to another, then click the "no" response and the program will be ended.

### FAQS: 

### What should you do if you plant was not in the list?
If the person ordering our product is skilled with github, they may provide us with a github repository. Our pi currently pulls a text file from our git repository every time the code is run, to determine which plants and asssociated thresholds to display. We can set the pi up to pull a specific text file from your repository instead. For this to work seemlessly, there must be no mistakes within how the repository or text file is named and what the pi is told to pull from. The text file also needs to be in the exact format where each line contains a plant name , plant threshold. The text file must look something like this:

<img width="230" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/c2bcaf3d-35ee-4940-a6a2-7d86dbc0692f">

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

<img width="450" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/3ee2c916-8743-4be6-8d7d-ef1feacda9e0">

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

<img width="552" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/5286c10d-38c8-4826-b173-9b75c59afb8f">

Before running anything, there is already an off-line version of plant_thresholds.txt stored in the folder. So even if RPi failed to download/pull, the rest of the program could still run. This is another nifty design choice on our end. This step attempts to download the plant_threshold.txt from GitHub to /home/pi/final0417 (where most of the codes lives). It then reports whether or not it was successful.

Here is an example of a successful report:

<img width="187" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/c42a6435-644f-49ba-87bf-b31c88a95517">

We chose to include this report so users can know their new file has been downloaded or that the pi is still running off of the old file because the new file failed to download. This could be useful for debugging purposes if someone tries to add a new plant and it doesn't show up, and they are perplexed as to why.

Step3: Readtxt02.py: read the plant_thresholds.txt downloaded from github and show plant choices on the screen for users to pick. The selection will be saved into file ‘new_plant_threshold.txt’
Some pygame window screenshots of this in action can be seen here:

<img width="327" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/13fb6724-a002-46c5-ab1f-1ace3255b797">
<img width="327" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/dd4f01a7-5098-409d-aa39-b8adecc56ef2">

After clicking ‘select’, the program will save the plant name and threshold in ‘new_plant_threshold.txt’.

Say we clicked, select on Test3, our 'new_plant_threshold.txt' file would look like this:

<img width="228" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/96377ff6-3d96-4f23-90cb-acfb7bd796c3">

This is used to save onto the current plant type and threshold associated with it. This file is used in the next code, which is also triggered after the save step.

For this python file, we specifically decided to display the plants individually (one oge at a time) with their thresholds. This is a very important design decision. If there were more than one plants per page, the page would need to be reformatted every time a plant type is changed or a new plant is added. Putting each plant on its own page means no reformatting is necessary. New plant just means an additional page to scroll through using the arrows. The code for this python file can be seen in our appendix.


Step 4: Test007_3.py: the main code for watering logic. 

This code reads the previous ‘new_plant_threshold.txt’ with default thresholds and allows users to change the threshold dynamically. 
The screen once this code is running can be seen here:

<img width="239" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/54f1ebc6-72a6-4504-9f92-b5622ec6c419">

As previously explained, sensor readings are displayed on the screen. 

Users can change the threshold by pressing the ‘up’ and ‘down’ on the screen. It goes up or down for 5% each time.

When the soil moisture level detected is lower than threshold and the water tank is not empty, the machine will start the water pump and show the green progress bar to assure it is watering.

<img width="78" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/9f3be0a9-ed69-4d6e-a19c-9d5a4cc8bf56">

It will then stop  watering once the moisture level has reached the threshold of the plant or above.
If water tank is empty, it will show a huge text in the top of the screen saying ‘Water Tank Empty’ and stop watering whether the moisture threshold is good or not.

The plant name and threshold used at the end of the program will be saved into ‘bad_plant_threshold.txt’ at the time it’s terminated by the quit button. The quit button is the right/bottom-most button on the piTFT. We chose to use a physical button, since it would still be functional if a screen issue were to take place.
If the quit button is pressed, the code will save current plant name and threshold to the ‘bad_plant_threshold.txt’ and exit. The code for this python file can be seen in our appendix.

Step 5: Report02.py: give user a choice to report bad threshold on their plants.

Step 5 displayes this screen using pygame:

<img width="209" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/cf0635cf-625e-4a1f-8f39-28e4390bcc78">

If the user chooses 'no', then the program will simply quit.

If the user chooses ‘yes’, a new txt file named ‘report_2023-05-10_19-45-06.txt’(for example), (The date and time will be the exact time), will be created and pushed to the GitHub repository. It would look like this:

<img width="332" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/dafadd62-3ba3-4ff1-989e-48d2876453e0">

We initally decided how we wanted the program to run from a user standpoint, aka what we wanted the screens to look like. This lead us to design our code as detailed above. A very early drawing of our screen idea can be seen beneath the code section in he "Additional photos" section.

The next design Section concerns hardware.


### Hardware

Here is an image of the circuit schematic and the actual circuit.

<img width="415" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/e6e67d4c-6d6f-49e1-97f3-c2dac0336e1b">

__picture__


We had already wired a motor driver for lab 3, so we felt this would be the best way to handle the water pump since this is a type of motor. We also decided to keep the light in the pwm line so that we could see whether the pwm signal was working as expected for any debugging purposes. The circuit is for the most part color coded. Grey represents ground and orange represents 3.3 V. Purple is the pwm line I just discussed as well as the output to the motor water pump. We chose to decide the pwm in for the motor driver last since certain GPIO pins need to be used for specific purposes. After setting up the sen ors and other which need specific pins, we chose GPIO pin 13 since it was unused and capable of pwm. This motor driver also needs an additional 5V power source to power the water pump. For lab 3, we had used the power supply. For this project, we wanted the system to be applicable in a modern day home. Most homes do not have power supplies. We purchased a female usb-c and soldered this to cables to attach to the motor driver. Now the motor driver can be powered using the same matching power chord as the one which powers the raspberry pi simply by pluggin one end into the wall and the usb-c end to our female usb-c.

The colorful lower pinout diagram belongs to the raspberyy pi. The pins whuch are squiggled out are already in use by the PiTFT. Therefore we cannot use them for anything else. The temperature sensor is the black box above that. Again the orange is 3.3V and the grey is ground. The blue wire is the SDA wire and the green wire is SCL. This uses the I2C channels. We chose to use I2C3 and actually tried I2C0 at one point as well, but the temperature sensor is left plugged into GPIO 4 for SDA3 (I2C3) and GPIO 5 for SCL3 (I2C3). 

Lastly the MCP3008 chip had to be plugged into the raspberry pi. This uses SPI instead of I2C. The chip can take up to 8 sensors. We only have two plugged in on channel 0 and 1. So in theory 6 more could be added before another chip is even needed. As you can see in the image, the water level sensor is plugged into channel 0 as well as 3.3V and ground, and the soil moisture sensor is plugged into channel 1 as well as 3.3V and ground. The chip also has a Vref and Vdd which are plugged into 3.3V (orange) and two grounds (AGND and DGND) which are plugged into ground (grey). The remaining yellow wires represent SCLK, Dout (MISO), Din (MOSI), and Chip select. WE decided to use SPI1 so we needed to plug these into the appropriate pins for SPI1. GPIO 16 is the Chip select pin for SPI1. GPIO20 is the MOSI pin for SPI1. GPIO 21 is the SCLK pin for SPI1, and GPIO 19 is the SPI1 MISO pin. All of this pretty much sums up the wiring and hardware.

## Results

We were able to complete this project in an acceptable manner. We definitely started out with big dreams and had to tone them down quite a bit. We had a base project that we felt was necessary to complete, then there were additions we wanted to possibly add if we had more time. For the most part
we did not get to these additions. These possibilities will be discussed more in the "Future Work" section. We were hindered by a few challenges which we will discuss next in the "challenges" section. We do feel as though we successfully completed this project since it does measure soil moisture and performs wonderfully at automatic watering when necessary. It also successfully reads the water level, and stops watering when the water source runs very low on water. Additionally, it is very possible to add any additional plants and to save date of dead plants. This system can definitely serve to keep a plant thriving and healthy per its watering needs. Proof of all this success can be seen in our demo video as well as throughout the website report here.

### Challenges

We unfortunately faced many challenges throughout this lab. 
The first challenge was time. we did have to order alot of parts, and we had to wait for these parts to come in. The code also took a long time to figure out and sort so it performed as expected.

Once we got the sensors in, we tried to set them up, and it didnt work. Thus begins the second challenge. We realized the raspberry pi only really defaulty enables one I2C and one SPI, which the PiTFT screen were using. We had to learn how to enable secondary channels (I2C3) and SPI2. We wire up the black soil moisture sensor and the red water level sensor to the MCP3008, then set up the MCP3008 to the SPI1 pins on the raspberry pi. We enabled SPI1 and were able to read the sensors!. We then continued to wire the temperature sensor into the I2C3 pins. We enabled I2C3, ran our code, and received an error. 

Challenge three was unfortunately one we did no overcome. The I2C3 did not work. We attempted to wire up to I2C0 and enable that, still not working. In theory it is enabled like so within the config.txt file: 

<img width="367" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/7a4b3025-22b2-4e92-9c71-a4b3014d2287">

Unfortunately, this uses the board library. If we check the directory of this library, Ther are no terms available to set the code to additional I2C channels as seen below:

<img width="365" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/d3cd78b6-cfb0-4c7d-bdbb-8db7115c5051">

You can see that for SPI there is a MISO and MISO_1, a MOSI and MOSI_1, etc. This means we can enable the SPI1 to those terms. When we attempt to enable I2C3, there is only one SDA and one SCL (the ones being used by the PiTFT, and there are no additional ones to use for the temperature sensor. We tried many things to solve this problem, but we could not solve the issue. We did have a minor issue initially with the sensor address (0x44) not even showing up on the I2C3 channel, but once we changed the sensor it shows up on the channel consistentley. There are just no terms in the board directory to be able to enable the SPI aSCL and SDA pins for this I2C3.


## Future Work

We had some initial ideas for the next phase of this project. First it would be best if we could get the temperature and humidity sensor working on I2C. We spent a lot of time and got a lot of help trying to figure this out, but nothing seemed to work. So, another solution is probably to buy a temperature and humidity sensor which uses SPI so that we can read them. This data can then be encorporated when a report is sent so we have additional information regarding why a plant might have died. Different plants also have different climates they grow best in which can be reflected by soil moisture, air humidity, and temperature, as well as other factors. We wrote our code so that these additional sources of information can be monitored as well as recorded. A threshold for a plant types air temperature and humidity can be easily include, and made alterable. The system could also then be set up to alert a user when they have left these desireable conditions for their plants.n Unfotunately our system would not be capable of altering the temperature and humoidity easily. Therefore, the air characteristics would have to be mended by the user. As discussed earlier, additional sensors could also be added. In our minds this includes a solar or light sensor as well as any wanted chemical sensors to monitor the ph level and chemical balances of the soil. Again te system could alert the user when any measured data is outside of the preferred threshold for a specific plant, but the user would have to mend this.


Further in the future we felt the automatic plant waterer could not only monitor and alert users to issues, but also mend them as it does with the soil moisture. These ideas would be more additional work than the inclusion of more sensors. One surrounds around using the temperature and humidity sensor in a greenhouse like environment. There could be heated lights to increase the temperature if necessary and fans to decrease the temperature or humidity as necessary, as well as a mister to increase humidity. These could be monitored and enabled when necessary by the system, but additional hardware might be necessary in setting all of this up. Another idea would be to use a curtain to shade and unshade a plant based off of the number of hours of sunlight is desired, and the hours of sunlight the solar sensor is reading. A motorr and some kind of mechanism to move the curtain would certainly be need as well as possibly other items. Honestly, this system could easily be customized by any user to do a many number of things.


## References

1. Happy plant photo: https://www.vecteezy.com/vector-art/3453255-happy-baby-plant-pot-cartoon-character
2. droopy sad plant photo: https://www.istockphoto.com/illustrations/dead-plants
3. brown sad plant photo: https://www.vectorstock.com/royalty-free-vector/dead-withered-plant-in-pot-ailing-dying-droopy-vector-46934145
4. MCP3008 wiring: https://learn.adafruit.com/raspberry-pi-analog-to-digital-converters/mcp3008
5. Temperature sensor wiring: https://learn.adafruit.com/adafruit-am2320-temperature-humidity-i2c-sensor/overview
6. Soil moisture: https://how2electronics.com/interface-capacitive-soil-moisture-sensor-arduino/
7. Water level sensor: https://lastminuteengineers.com/water-level-sensor-arduino-tutorial/

## Code Appendix



## Additional Photos

<img width="600" alt="image" src="https://github.com/samanthaccole243/AutomaticPlantWaterer/assets/89661904/24b3e14c-08d6-4aae-8dee-1fa99195037a">

