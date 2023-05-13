### Do you love plants, but always have them end up looking like this? 


<img width="299" alt="image" src="https://user-images.githubusercontent.com/89661904/236704407-b3c708fd-3550-4f1b-8e71-5645bf7ebfcb.png"> <img width="530" alt="image" src="https://user-images.githubusercontent.com/89661904/236704478-69dfd48c-00a6-4b79-8df5-cdbd6248e2e8.png">




 ### Look no Further! 
  

!Warning!
This Project will solve all your plant problems 

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

### Screen displays

Now we can examine what happens on the raspberry pi for the automatic plant waterer to function. After pluggin in the raspberry pi, it should turn on. Run the program, as seen in the video by typing ___________________help___. Then you will see a screen with a plant name, a select button and some arrows. The screen will look something like this:

___picture____

Using the arrows, navigate through the different plant options, and choose the plant you are trying to water automatically. If your plant is not there, no problem. You can either watch our video for more details on how to handle this or scroll down to the "What to do if you plamt is not in the initial list" section, then return here when finished.

Once you have found the screen with your desired plant, click select. A screen similar to the image below should appear.

__picture___

This screen displays the air moisture and temperature as measured by the humidity and temperature sensor. Unforutnately for the current model, we were not able to actually get this sensor working appropriately. We will discuss this more in the "Challenges" section. Therefore, the screen simply displays room temperature and 50% percent humidity for now. Next the soil moisture sensor reading can be seen. This number will change slightl as the sensor will contain a bit of noise. The number will also increase drastically after watering, since the soil will be much more moist. The next line confirms that the water level is okay. Then the threshold for the particular plant is displayed. The user has the option to either increase or decrease the threshold according to their will. Just remember that the threshold originally set for that plant is recommended and any changes might starve or drown your plant. We do recognize however that some plants vary and you might want to be able to control the threshold yourself. 

