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

<h2>TODO:</h2>
SHOW_NETS:              //  SHOW WIFI NETS AVAILABLE<br>
SET_CREDENTIALS:        //  SET WIFI CREDENTIALS <br>



<h2>HTTP Services Implemented:</h2>

The following HTTP services are implemented: 
  /SaveCredentials"       <br>
  /GetLightState"         <br>
  /SetLightsOn"           <br>
  /SetLightsOff"          <br>
  /getNetworksKnownByDev" <br>


<h3>XMLHTTPRequest (JavaScript) Code Samples:</h3><br>

<b>/SaveCredentials</b><br>
<ul>
<li>TimeStamp</li>
<li>SSID</li>
<li>Passwd</li>
<li>SystemID</li>
</ul>

<pre>
In this example TimeStamp = 23/11/2016 15:42

var data = "TimeStamp=23%2F11%2F2016%2015%3A42&SSID=mySSID&Passwd=myPasswd&SystemID=mySystemID";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "http://192.168.1.18/SaveCredentials?SystemID=mySystemID&Passwd=myPasswd&SSID=mySSID&TimeStamp=22%2F01%2F2017");
xhr.setRequestHeader("content-type", "application/x-www-form-urlencoded");

xhr.send(data);
</pre>

<b>/GetLightState</b><br>
<ul>
<li>TimeStamp</li>
<li>Command=GetLightState</li>
</ul>

<pre>
var data = "TimeStamp=29%2F05%2F2017%2022%3A12&Command=GetLightState";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === this.DONE) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "http://192.168.1.18/GetLightState");
xhr.setRequestHeader("content-type", "application/x-www-form-urlencoded");

xhr.send(data);
</pre>

