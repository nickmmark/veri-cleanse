# veri-cleanse proof of concepts
These are small projects meant to illustrate the incremental early steps necessary to build the fully featured device.

### POC #1
### POC #2 -
* ***Goal***: Soap dispenser that can upload data to the cloud - 
* ***Hardware***: an ESP8266 that can detect soap dispenser activation an upload a data packet

### POC #3

### POC #4 
* ***Goal***: demonstrate the ability to trigger a soap dispenser
* ***Hardware***: ESP32 connected to a servo activates a transient 6V current to the soap dispenser motor
  * Soldered two pairs of wires onto the main board of the soap dispenser: connected to motor and to the IR sensor.
  * Connected the setup together like this:

<img src="https://github.com/nickmmark/veri-cleanse/blob/master/POC/figures/soldered_connections.jpeg" width="300">

![wiring diagram](https://github.com/nickmmark/veri-cleanse/blob/master/POC/figures/POC4_wiring.png)

* ***Code***: based upon the ESP32 web server demo, configured to activate a relay or LED

```C++
#include <WiFi.h>               // load wifi library
const char* ssid     = "xxx";   // store network credentials
const char* password = "yyy";
WiFiServer server(80);          // Set web server port number to 80
WiFi.begin(ssid, password);     // connect to wifi
```


* ***Demonstration***:

![demonstration](https://github.com/nickmmark/veri-clean/blob/master/POC/figures/poc_demo_remote_control.gif)

* ***Other notes***:


### references
