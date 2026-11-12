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
In today’s weekly work session, we combined the 3D-printed scanner casing with the scanner. This allowed us to see how the 3D-modeled case fits with the scanner hardware and how the two parts work together.

The 3D-printed object has an interesting, distinctive shape, but it needs some reworking. As of now the design is a bit uncomfortable for different users, since hand sizes and grip styles vary. Adjusting the edges and proportions would make it more easier to hold for longer periods.

The scanner itself also needs some refinement, because its readings are currently somewhat inaccurate. Sometimes a colour is shown but the sound playing does not correspond to the correct colour. Improving the code and checking the sensor placement inside the case would be important steps so we can reach a better prototype.


Videos and Images from this week's work session.
https://github.com/user-attachments/assets/b5d33300-16ab-4187-bcac-1f637081c273


<img width="1000" height="742" alt="image" src="https://github.com/user-attachments/assets/97cdc7fd-1973-443a-9ee9-f51cd6599155" />
<img width="585" height="785" alt="image" src="https://github.com/user-attachments/assets/efc25a0b-d0b4-4a84-b5f4-da0d19266cfd" />

Below are some screenshots documenting the design and development process of the 3D model that holds the scanner.

<img width="782" height="762" alt="image" src="https://github.com/user-attachments/assets/86b7de7f-111a-466e-aadb-3fcd7add4b6c" />
<img width="692" height="757" alt="image" src="https://github.com/user-attachments/assets/abfac77c-dbfa-47fb-af60-65adca24c92d" />
<img width="630" height="407" alt="image" src="https://github.com/user-attachments/assets/f504d596-4991-49d6-ac3a-c70ed751d678" />


## Journal week 7
This week, we worked on creating the presentation and divided the tasks evenly among team members. We also had our client meeting with Nadia, who mentioned that she would like a way to use the scanner wirelessly. To make this possible, we will look into the different tools needed to connect the Arduino and the scanner piece so that they become a standalone, battery-powered device. This will also make the scanner easier to demonstrate and use outside of a lab setting.

Because of the nature of the project, we need to know what the tapestry will look like, specifically its colours, so we can refine the scanner’s readings to detect different hues and shades. Nadia told us that we would be working with a tapestry that is somewhat feminine, with pinks and reds as the main colours. Since those shades are close together, the scanner will need to distinguish between subtle differences in colour. She also offered to create a small prototype for us, although we are not sure whether she will have enough time to finish it before our final demo. In the meantime, we may need to test with our own version of a tapestry.

Below are the notes from our meeting with Nadia:
```
MAIN CHANGES:
Prototype: She prefers that the scanner sensor not be connected to the computer. Essentially, making it its own device. Besides preferences, the reasoning is that she can easily scan the tapestry without having the laptop nearby.
Potential Solution: The scanner uses batteries instead

Box design: She didn’t like the design, as the width was too big and made the box awkward to hold. The main concern with the box itself was the width and shape. 
Potential Solution: Nadia liked the idea of changing the shape to a cylinder so it looks better and is easier to hold. The difference is that we’ll be adding more components to run it on batteries; therefore, the cylinder design might need to be longer. 


Pending info:
3D designing the tapestry: Nadia said she was going to consult with someone about whether she will provide the tapestry or if we’ll make one
Song audio
Alternative option: poem audio

Extra:
In case the initial idea of having the song audio doesn’t work as planned, she said suggested we can use the audio of a poem instead.

```

Here's our updated code for the project:

**Arduino Code**

```
/*
  AS7265x Spectral Color Classifier + Continuous Audio Trigger
*/


#include "SparkFun_AS7265X.h"
AS7265X sensor;


void setup()
{
  Serial.begin(115200);
  Serial.println("AS7265x Spectral Color Classifier Initializing...");


  if (sensor.begin() == false)
  {
    Serial.println("Sensor does not appear to be connected. Freezing...");
    while (1);
  }


  Serial.println("A,B,C,D,E,F,G,H,R,I,S,J,T,U,V,W,K,L");
}


void loop()
{
  sensor.takeMeasurements();


  float a = sensor.getCalibratedA();
  float b = sensor.getCalibratedB();
  float c = sensor.getCalibratedC();
  float d = sensor.getCalibratedD();
  float e = sensor.getCalibratedE();
  float f = sensor.getCalibratedF();
  float g = sensor.getCalibratedG();
  float h = sensor.getCalibratedH();
  float r = sensor.getCalibratedR();
  float i = sensor.getCalibratedI();
  float s = sensor.getCalibratedS();
  float j = sensor.getCalibratedJ();
  float t = sensor.getCalibratedT();
  float u = sensor.getCalibratedU();
  float v = sensor.getCalibratedV();
  float w = sensor.getCalibratedW();
  float k = sensor.getCalibratedK();
  float l = sensor.getCalibratedL();


 
  printValues(a, b, c, d, e, f, g, h, r, i, s, j, t, u, v, w, k, l);


 
  int currentTrack = classifyColorToTrack(c, e, f, g, r, a);


  triggerAudio(currentTrack);


  delay(200);
}




void printValues(float a, float b, float c, float d, float e, float f, float g, float h, float r, float i, float s, float j, float t, float u, float v, float w, float k, float l) {
  Serial.print(a); Serial.print(",");
  Serial.print(b); Serial.print(",");
  Serial.print(c); Serial.print(",");
  Serial.print(d); Serial.print(",");
  Serial.print(e); Serial.print(",");
  Serial.print(f); Serial.print(",");
  Serial.print(g); Serial.print(",");
  Serial.print(h); Serial.print(",");
  Serial.print(r); Serial.print(",");
  Serial.print(i); Serial.print(",");
  Serial.print(s); Serial.print(",");
  Serial.print(j); Serial.print(",");
  Serial.print(t); Serial.print(",");
  Serial.print(u); Serial.print(",");
  Serial.print(v); Serial.print(",");
  Serial.print(w); Serial.print(",");
  Serial.print(k); Serial.print(",");
  Serial.print(l);
}




int classifyColorToTrack(float blueC, float greenE, float greenF, float greenG, float redR, float baseLine) {
  float totalIntensity = blueC + ((greenE + greenF + greenG) / 3.0) + redR;
  if (totalIntensity < 15.0 || baseLine == 0.0) {
    return 1; // Track 1 -> BLACK
  }


  float greenScore = (greenE + greenF + greenG) / 3.0;
  float adjustedGreen = greenScore * 1.2;


  if (blueC > adjustedGreen && blueC > redR) {
    return 2; // Track 2 -> BLUE
  }
  else if (adjustedGreen >= blueC && adjustedGreen >= redR) {
    return 3; // Track 3 -> GREEN
  }
  else {
    return 4; // Track 4 -> RED
  }
}




void triggerAudio(int trackNumber) {
  Serial.print(" | PLAY_TRACK:");
  Serial.println(trackNumber);
}

```
**Python Code**
```

import serial
import time
import winsound
import os




script_dir = os.path.dirname(os.path.abspath(__file__))


SERIAL_PORT = 'COM4'  
BAUD_RATE = 115200


print(f"connect Arduino，port: {SERIAL_PORT}...")


last_played_track = None
last_play_time = 0
COOLDOWN_TIME = 1.0  


try:
    ser = serial.Serial(SERIAL_PORT, BAUD_RATE, timeout=1)
    print("successful...")


    while True:
        if ser.in_waiting:
            line = ser.readline().decode('utf-8', errors='ignore').strip()
           
            if "PLAY_TRACK:" in line:
                track_num = line.split("PLAY_TRACK:")[1].strip()
                current_time = time.time()
               
                if track_num != last_played_track or (current_time - last_play_time > COOLDOWN_TIME):
                    if track_num != last_played_track:
                        print(f"==> switch color {track_num} ...")
                    else:
                        print(f"==> reconnect {track_num}...")
                       
                   
                    audio_filename = os.path.join(script_dir, f"{track_num}.wav")
                   
                    try:
                       
                        winsound.PlaySound(None, winsound.SND_PURGE)
                        winsound.PlaySound(audio_filename, winsound.SND_FILENAME | winsound.SND_ASYNC)
                       
                        last_played_track = track_num
                        last_play_time = current_time
                    except Exception as e:
                        print(f"error: {e}")


        time.sleep(0.05)


except serial.SerialException:
    print(f"cant not connect {SERIAL_PORT}。double check Arduino IDE ！")
except KeyboardInterrupt:
    print("\nexit...")


```

Dika created a list of items that should be purchased for this project, shown below:
<img width="1207" height="842" alt="image" src="https://github.com/user-attachments/assets/2bd907e3-8e9d-4583-9164-284c63b84824" />


## Journal week 8
We presented our work in our last class and received feedback from our peers, which helped us get a broader perspective. We also received the new parts that Nadia ordered, which will allow us to use the scanner as a standalone device without needing to connect it to a laptop. This allows to create a wireless, battery-powered setup that Nadia asked for.

We received the audio that the client wanted to use for this project. We will need to figure out how it will be integrated with the scanner so that it plays as part of the final experience. As of now we were thinking of having certain words play when a certain shade or colour or shown but this idea still needs to be developed. 

[Link to the audio](https://soundcloud.com/kinawind/dont-cry-baby-rita-starr-complete?utm_source=clipboard&utm_medium=text&utm_campaign=social_sharing)

## Journal 9
I couldn't make it to todays class meeting but our teammates wrote some notes.
```
notes 👍

Technology and artist work, low fidelity prototype, why going in that direction?
Background
Thinking deeply from the sounds and how it can be twisted, unusual that will surprise the audience. The choice of the sound with her vision. 

Continue of the work, how it will fit with her work, similar to her work. Affective quality of the work.  

```

## Journal 10


## Journal 11
