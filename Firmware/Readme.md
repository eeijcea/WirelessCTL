<h2>Binary compiled for a: </h2>
<br>NodeMCU 1.0 ESP-12E || CPU Frequency: 80 MHz || Flash Size: 4M (3M SPIFFS)||Serial Speed: 115200<br><br>

The Firmware provided implements some command line interface (CLI) services as well as Web Services (See below). It is capable to expose a Wifi where you can connect for consume WebServices or you can attach it to your Home Wifi Network<br>

<b>When in Local Wifi Mode</b><br>
SSID: WirelessCTL<br>
PASSWD: hotIcon123<br>

<b>When attached to your Wifi Network</b><br>
Use your own credentials.<br>

However, to set the Credentials of your Home Wifi the very first time you will need:<br>
1) Attach in Local Wifi Mode (Above)<br>
2) Using an Internet Browser invoke the SaveCredentials Web Service as described below in 
SaveCredentials section.<br>

Hint: 192.168.4.1 is the Default NodeMCU Ip Address when running in Local Wifi Mode<br>

<b>Sample Request:</b><br>
http://192.168.4.1/SaveCredentials?SystemID=mySystemID&Passwd=myPasswd&SSID=mySSID&TimeStamp=22%2F01%2F2017<br>




<h2>Tool for Upload firmware to your NodeMCU:</h2>
<a href="https://github.com/nodemcu/nodemcu-flasher">NodeMCU Flasher</a>


<h2>CLI Services Implemented:</h2>     
Accesible via Serial NodeMCU (usb) from Arduino IDE<br>
<ul>
<li>SHOW_DEVICEID:          //  SHOW DEVICEID</li>
<li>SHOW_HISTORY:           //  <a href="https://github.com/eeijcea/WirelessCTL/blob/master/Firmware/SHOW_HISTORY.png">SHOW REQUESTS HISTORY</a></li> 
<li>SHOW_CREDENTIALS:       //  SHOW WIFI CREDENTIALS (IF SET)</li>
<li>RESET_HISTORY:          //  PERFORMS A HISTORY RESET</li>
<li>SET_RESET:WIFI:         //  PERFORMS A CREDENTIALS FILE RESET</li>
</ul>

<h2>TODO:</h2>
<ul>
<li>SHOW_NETS:              //  SHOW WIFI NETS AVAILABLE</li>
<li>SET_CREDENTIALS:        //  SET WIFI CREDENTIALS</li>
</ul>


<h2>HTTP Services Implemented:</h2>

The following HTTP services are implemented: <br>
  /SaveCredentials       <br>
  /GetLightState         <br>
  /SetLightsOn           <br>
  /SetLightsOff          <br>
  /getNetworksKnownByDev <br>


<h3>XMLHTTPRequest (JavaScript) Code Samples:</h3><br>

<h3><b>/SaveCredentials</b></h3>
<p>This service allows you to save to NodeMCU your Wifi Credentials (SSID and Password), it also allows us you to save a friendly ID (SystemID) for your embedded system.</p><p>Input Parameters:</p>
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

<h3><b>/GetLightState</b></h3>
<p>This service allows you to retrieve current NodeMCU output pin status (the one used for set On/Off). Be aware that currently firmware is memoryless, this basically means even if last command submitted was Power ON if a reset happens in the middle system will not reflect this.</p>
<p>Input Parameters:</p>
<ul>
<li>TimeStamp</li>
<li>Command=GetLightState</li>
</ul>

<pre>
In this example TimeStamp = 29/05/2017 22:12

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

