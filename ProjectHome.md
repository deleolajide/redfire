# Redfire #

<p>Redfire is a plugin for Openfire that embeds the <a href='http://code.google.com/p/red5'>Red5 RTMP server</a>, <a href='https://github.com/OpenRTMFP/Cumulus'>Cumulus RTMFP server</a> and modified <a href='http://phono.com/'>Phono SDK</a> to provide audio/video streaming tools for XMPP application development.</p>

![http://redfire.googlecode.com/files/Image1.jpg](http://redfire.googlecode.com/files/Image1.jpg)

## It provides the following: ##

  * An RTMP server (Red5) that can be used to deliver TCP audio/video media along side XMPP messaging and signalling.

  * An RTMFP server (Cumulus) that can be used to deliver peer to peer UDP audio/video media along side XMPP messaging and signalling. **It is disabled by default as only binary for Windows is provided. Linux users must download and build the binary from source**

  * A plugin for Spark.

  * A modified version of the Phono SDK to make phone calls from a web browser with JavaScript and jQuery.

  * A Java web start application that captures and publishes the desktop screen as an RTMP video stream.

  * 2 person audio/video conversation web page

  * 12 persoon audio/video conferencing web page


![http://redfire.googlecode.com/files/Image3.png](http://redfire.googlecode.com/files/Image3.png)

## How to use ##

  * Stop Openfire

  * Unzip redfire-x.x.x.x.zip  and copy the redfire.war file to the OPENFIRE\_HOME/plugins directory

  * Restart Openfire

  * From a browser, go to http://your_openfire-server:7070/redfire

  * For Spark Plugin, download from http://your_openfire-server:7070/redfire/spark/redfire-plugin.jar

## How to setup PSTN/PBX gateway for external phone calls ##

To setup a PSTN/PBX gateway for external VOIP telephone calls, use the SIP plugin to setup the SIP account and add the follwing two properties to Openfire. Use the standard admin user or any other admin account..

|Property|Default Value| |Description| |
|:-------|:------------|:|:----------|:|
|<b>voicebridge.default.proxy.name</b>|

&lt;required&gt;

| |A unique name for Voice bridge external PSTN Gateway. If missing, no PSTN gateway is available.| |
|<b>voicebridge.default.proxy.username</b>|

&lt;required&gt;

| |XMPP username used to create the SIP registration by SIP plugin| |

![http://openfire-candy.googlecode.com/files/Image8.jpg](http://openfire-candy.googlecode.com/files/Image8.jpg)

## How to enable Cumulus ##

  * Stop Openfire
  * Edit OPENFIRE\_HOME\plugins\redfire\WEB-INF\web.xml. Remove comments
```
<!--
	<servlet>
		<servlet-name>CumulusServlet</servlet-name>
		<servlet-class>com.ifsoft.redfire.servlets.CumulusServlet</servlet-class>
		<load-on-startup>4</load-on-startup>
	</servlet>
-->
```

  * Edit OPENFIRE\_HOME\plugins\redfire\video\redfire\_2way.html and redfire\_video.html. Edit rtmfpUrl to point at your Openfire server

```
var rtmfpUrl	= getPageParameter('rtmfpUrl', 'rtmfp://' + window.location.hostname + '/');
//var rtmfpUrl	= getPageParameter('rtmfpUrl', '');

```

  * Edit OPENFIRE\_HOME\plugins\redfire\phono\index.html. Enable RTMFP for Redfire-Phono
```
   		  <select class="audio-plugin">
                    <option value="flash">Flash (Red5 - RTMP)</option>
                    <option value="panda">Flash (Cumulus - RTMFP)</option>
   		  </select>
```

## Support and more Information ##
  * For more information and support for redfire go to http://community.igniterealtime.org/community/plugins/red5

  * For more information about red5 go to http://code.google.com/p/red5

  * For more information about openfire go to http://www.igniterealtime.org