# CART-470

## Journal Entry week 2(09.22.2026)
Last class we had our first team brainstorm session and we were able to discuss the project that we were assigned to. We used posts-its and came up with different questions and ideas we have for our client.

<img  alt="image" width="500" height="500" src="https://github.com/user-attachments/assets/c3f8bd25-9ab9-49bb-ac34-4afe18664893" />

Tasks for next week
- define our roles within the team
- create the living learning contract
- organize kanban board with different tasks
- continue brainstorming questions 

## Journal Week 3 (09.22.2026)
This week we met with the client we had the opportunity to understand more what the project is about. Our client wants us to use ceramics and tools that **feel mechanical rather than use a software or third party source**. Our client wants us to be able to come up with a project that will be able to play a song directly. They gave us tools that we can use for inspiration for example a wax cylinder, which is a recording tool used in indigenous cultures to capture sound recordings and playing them back. 

We want to explore different ways of satisfying the client's project requirements. We will be meeting with our client in their studio, on a weekly basis to go over our progress and findings. 

We created the living learning contract to ensure that our team is aware of what our project needs and what do we want to take away from this project. 


Tasks for next week:
- defining our roles within the group
- staying up to date with the Kanban board
- start research



## Journal Week 4 (09.22.2026)

This week we defined what our project would be. We are creating a prototype that has a scanner that will play audio based on the colour of the tapeestry. The inspiration for the scanner came from this reddit forum where someone uses a scanner to display different colours on the screen based on where the scanner is placed.
[link to the video](https://www.reddit.com/r/arduino/comments/ntjxde/make_your_own_color_sensor_the_lowest_cost_and/)

We plan on using a couple tutorials found online like the ones below:
- [link to first video](https://www.youtube.com/watch?v=Ey5UhCxlxis)
- [link to second video](https://www.youtube.com/watch?v=EeeWH_kBWwc&pp=ygUnY29sb3VyIGRldGVjdGlvbiB1c2luZyBhcmR1aW5vIHRjczM0NzI1)



The scanner hovers over the tapestry and sound comes from it. Allowing interaction with the piece and the viewer. We plan on 3D printing pieces to resemble the typical material's that our client uses for their artworks. Our client has a 3D clay printer in their studio that we could use for this project, or if we choose to not go with clay printing we can use the 3D printers that are offered in the Concordia library. 

At today's team meeting we defined what our roles would be in our group. This will help us stay more organized and understand what we will all contribute to the project. 

<table>
  <thead><th>Role</th><th>Members</th></thead>
  <tr><td>3D Printing Model</td><td>Bianca & Sophie</td></tr>
  <tr><td>Arduino Scanner</td><td> Dika & Terence & Jolene</td></tr>
  <tr><td>Midi Instrument/Audio</td><td>Namiko</td></tr>
  <tr><td>Assistant Project Manager</td><td>Jolene</td></tr>
</table>

Tasks for next week 
- 3d printing team should be working on designs
- namiko should explore how we can use the midi instrument to translate it to colour
- scanner team will meet up to start assembling and testing scanner options



## Journal Week 5

During reading week Dika, Terence and I met on campus in the computation lab to work on the scanner. We used the TCS34725 sensor and an arduino to create our sensor. When we started to do the wiring we kept getting an error message saying the sensor couldn't be detect it. We tried switching microcontrollers and switching the cables but it only started working once we soldered the sensor on the breadboard.

first code snippet we used
```
//project 1 - RGB color sensor 
#include <Wire.h> 
#include "Adafruit_TCS34725.h"

// Create an instance of the TCS34725 sensor 
Adafruit_TCS34725 tcs = Adafruit_TCS34725(TCS34725_INTEGRATIONTIME_614MS, TCS34725_GAIN_1X);

void setup() { 
  Serial.begin(9600);

if (tcs.begin()) { 
  Serial.println("Found TCS34725 sensor"); 
  } 
else { 
    Serial.println("No TCS34725 found ... check your connections"); 
    while (1); // halt the program 
    } 
  }

void loop() { 
  uint16_t r, g, b, c; 
  tcs.getRawData(&r, &g, &b, &c);

// Check if there is significant color detected 
  if (c > 50) {   // Adjust the threshold as needed 
  // Normalize the values 
  float sum = c; 
  float red = r / sum; 
  float green = g / sum; 
  float blue = b / sum;

Serial.print("R: "); Serial.print(r); Serial.print(" ");
Serial.print("G: "); Serial.print(g); Serial.print(" ");
Serial.print("B: "); Serial.print(b); Serial.print(" ");
Serial.print("C: "); Serial.print(c); Serial.println(" ");

// Calculate the color temperature and lux
uint16_t colorTemp = tcs.calculateColorTemperature(r, g, b);
uint16_t lux = tcs.calculateLux(r, g, b);

Serial.print("Color Temp: "); Serial.print(colorTemp, DEC); Serial.print(" K - ");
Serial.print("Lux: "); Serial.println(lux, DEC);

// Determine the color
if (red > green && red > blue) {
  Serial.println("Detected Color: RED");
} else if (green > red && green > blue) {
  Serial.println("Detected Color: GREEN");
} else if (blue > red && blue > green) {
  Serial.println("Detected Color: BLUE");
} else {
  Serial.println("Detected Color: UNKNOWN");
}
} else { Serial.println("No significant color detected"); 
}

// Wait for 2 seconds before the next reading
 delay(2000); 
}
```
Once we got it to work we realized that the readings weren't working correctly




https://github.com/user-attachments/assets/4be3c6f8-67dd-418e-bda1-b50085780ac2



## Journal Week 6
We combined the 3D printed scanner with our version of it. The 3D printed object has an interesting shape but it needs some reworking due to how it could be uncomfortable for different people.

## Journal week 7
This week we worked on creating the presentation and splitting our tasks evenly for the presentation. we had our client meeting 

