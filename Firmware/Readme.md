<h2>Binary compiled for a: </h2>
<br>NodeMCU 1.0 ESP-12E || CPU Frequency: 80 MHz || Flash Size: 4M (3M SPIFFS)||Serial Speed: 115200


<h2>CLI Services Implemented:</h2>     
Accesible via Serial NodeMCU (usb) from Arduino IDE<br>
<ul>
<li>SHOW_DEVICEID:          //  SHOW DEVICEID</li>
<li>[SHOW_HISTORY:](https://github.com/eeijcea/WirelessCTL/blob/master/Firmware/SHOW_HISTORY.png)           //  SHOW REQUESTS HISTORY</li>
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
  /SaveCredentials"       <br>
  /GetLightState"         <br>
  /SetLightsOn"           <br>
  /SetLightsOff"          <br>
  /getNetworksKnownByDev" <br>


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

