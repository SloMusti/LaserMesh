# LaserMesh
Laser based mesh communication is the idea fo creating a simple low-speed communication network between low cost electronics devices, likely ESP8266 WiFI module boards to be able to visualize and recreate in 3D the netowrk connectivity in actual WiFi mesh network but at a room-scale.

## Laser modulation and communication basics
The followign link is a msut read about laser modulation and long distance communications: http://www.modulatedlight.org/optical_comms/using_laser_pointers.html The basic intro reading on modulation is well collected here: http://www.repairfaq.org/sam/laserdio.htm#diodelp

## Data-link
The most optimal use-case would be for every laser link to be able to send data between the nodes to ahve an actual direct optical communication, however that is not actually necessary for the basic use-case of vizualization.

Red laser pointers can be modulated most definitely to a few Mhz if not more, depending on the internal electronics and construction, that being sufficient for a simple data-link.

* Simple uart link example: http://jmp.no/blog/laser-driven-optocoupled-uart
* There is a way how to go to 1Gbps https://www.extremetech.com/extreme/128207-1gbps-wireless-network-made-with-red-and-green-laser-pointers
* RS232 laser link from 1997: http://www.qsl.net/n9zia/wireless/laser/laser.htm
* 100m+ simple audio link https://www.youtube.com/watch?v=MCTqC2-AN7o

## Hardware
 To send and receive, we need basically a laser pointer and a optical detector. Low-cost laser module with modulation input explained here: http://henrysbench.capnfatz.com/henrys-bench/arduino-output-devices/ky-008-arduino-laser-module-guide-and-tutorial/
 
 Interestingly, laser sensor module for obstacled apparently modualted at 180kHz http://www.waveshare.com/laser-sensor.htm, has a receiver and transmiter on it which we could use with alternative electronics.
 
 A solar cell can be used as a receiver, the following paper determines the bandwidths: http://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7010358 so a link up to about 10Mbps is feasible with solar cells. Expansion on building a VLC sensor system from this: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4813993/
 
 # Design choices
 A brief review of the technology shows us that modulating red lasers is feasible in the 1+ MHz range without significant challenges and that simple solar cells can be used as receivers as well as a power source. The design of our mesh can be a bit differen in terms on multi-transmitter and single receiver architecture per module, nicely coupling with the serial communication protocol if the software can handle collisions or operate with sufficiently low air-time.
 
 Summarized:
 * Arduino compatible processor, best ESP8266 module
 * Multi TX, feasible with Soft UART, single RX with hardware UART
 * Red laser module/pointer for TX
 * Solar cell as RX
 * Battery or USB power
 * [Flex tube for laser mounting]( https://www.aliexpress.com/store/product/White-1-4-12mm-Thread-Diameter-Flat-Nozzle-Flexible-Coolant-Pipe/1728029_32350960894.html)
 
