<h2>NodeMCU 1.0 ESP-12E </h2>
Binary compiled for a: <br>CPU Frequency: 80 MHz
Flash Size: 4M (3M SPIFFS)
Serial Speed: 115200


<h2>CLI Services Implemented:</h2>     
Accesible via Serial NodeMCU (usb) from Arduino IDE
SHOW_DEVICEID:          //  SHOW DEVICEID<br>
SHOW_HISTORY:           //  SHOW REQUESTS HISTORY<br>
SHOW_CREDENTIALS:       //  SHOW WIFI CREDENTIALS (IF SET)<br>
RESET_HISTORY:          //  PERFORMS A HISTORY RESET <br>
SET_RESET:WIFI:         //  PERFORMS A CREDENTIALS FILE RESET<br>

<h2>HTTP Services Implemented:</h2>

The following HTTP services are implemented: 
  /SaveCredentials"       <br>
  /GetLightState"         <br>
  /SetLightsOn"           <br>
  /SetLightsOff"          <br>
  /getNetworksKnownByDev" <br>


<h3>/SaveCredentials:</h3>
XMLHTTPRequest (JavaScript) Example:<br>
<ul>
<li>TimeStamp</li>
<li>SSID</li>
<li>Passwd</li>
<li>SystemID</li>
</ul>

var data = "TimeStamp=23%2F11%2F2016%2015%3A42&SSID=GUZMAN&Passwd=5433358510&SystemID=eGarden-01";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://192.168.1.18/SaveCredentials?SystemID=eGarden-01&Passwd=5433358510&SSID=GUZMAN&TimeStamp=22%2F01%2F2017");
xhr.setRequestHeader("content-type", "application/x-www-form-urlencoded");


xhr.send(data);

<h2>TODO:</h2>
SHOW_NETS:              //  SHOW WIFI NETS AVAILABLE<br>
SET_CREDENTIALS:        //  SET WIFI CREDENTIALS <br>

