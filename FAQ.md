| Copyright (C) 2009 The Sipdroid Open Source Project. The following article is part of Sipdroid. Sipdroid is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version. |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|



## Prerequisites ##

### How can I prepare for mobile VoIP? ###

Sipdroid allows you to choose where you will use VoIP, on WLANs only, on 3G, or EDGE networks. If you are going to use VoIP services outside private wireless networks, it's your responsibility to check the contractual terms with the mobile operator:

Often mobile phone operators forbid using VoIP in the contract's fine print. The European Union is already looking at whether blocks on VoIP service by Europe's mobile phone operators might breach competition laws.

The following plans are suitable for unlimited hotspot/3G usage:

  * USA: "T-Mobile has **no restrictions** on using SIP as a signaling protocol." ([source](http://groups.google.com/group/android-developers/browse_thread/thread/9e471b66e7f397b1/d5051b3d37c79beb?hl=en&ie=UTF-8&q=sipdroid#d5051b3d37c79beb))
  * Germany: [debitel Talk and Surf S](https://www.debitel.de/privat_shop/mobilfunk/tarife/uebersicht/tariftabelle/debitel-talk-and-surf-s-im-dt.-t-mobile-netz-22723.php), all T-Mobile and Vodafone plans with VoIP Option, and all [O2 customers with Internet Packs](http://www.de.o2.com/ext/o2/wizard/index?page_id=15698;tree_id=303;category_id=;year=;page=1;state=online;style=portal)

[Add](http://code.google.com/p/sipdroid/w/edit/FAQ) more!

### What type of warranty comes with Sipdroid? ###

This project publishes Sipdroid for free under the terms of [GNU General Public License v3](http://www.gnu.org/licenses/gpl.html). The first public version is beta for software testing. So please allow for some issues and incompatibilities at the beginning.

### How much will Sipdroid drain the battery? (Constantly running Internet connection?) ###

When using [pbxes.org](http://pbxes.org) the expected stand-by times are the same as without Sipdroid running in the background (we observed about three days of stand-by time).  See [article](http://code.google.com/p/sipdroid/wiki/NewStandbyTechnique) for background.

### How much bandwidth is required? ###

Sipdroid uses G.711 A-law to transmit voice which needs about 80 kBit/s in each direction. This corresponds to a total of 1.2 MB per minute.

A video call needs approximately twice as much.

Over EDGE or when optionally enabled for all calls Sipdroid uses GSM codec to compress to about 30 kBit/s in each direction resulting in a total of 0.5 MB per minute.

### What are the system requirements? ###

To install Sipdroid you need version 1.5 "Cupcake" of Android.

See http://android-developers.blogspot.com/2009/04/android-15-is-here.html for details on updating the OS on developer phones.

The update for the other phones comes over the air, starting May 1st, 2009.

### What build environment is needed for Sipdroid? ###

If you are interested in developing and contributing to the project please install [Eclipse](http://developer.android.com/sdk/1.1_r1/installing.html) and [Subclipse](http://subclipse.tigris.org/install.html) for building the source code.

After the sources are done downloading, you see the following in "Package Explorer"
in Eclipse.

> SipUA 326 [Trunk: trunk](http://sipdroid.googlecode.com/svn,)

Right click on SipUA and select Properties in the drop down menu (last option). Click
on Android (assumes the Android SDK is installed and configured in Eclipse). In the
"Project Build Target" select "Android 1.6" (Target Name).

## User Interface ##

### How can I dial my contacts over Sipdroid / over Phone? ###

In settings you can specify your preferred call type. This is used when clicking a "Call" tab of a contact. When clicking on the "Text" tab of a contact you get a menu like this:

![http://sipdroid.googlecode.com/svn/images/choose.png](http://sipdroid.googlecode.com/svn/images/choose.png)

"Messaging" lets you proceed with sending SMS/MMS. The other two let you override your call type manually.

### How can I dial a number over Sipdroid / over Phone? ###

When entering a phone number in the dialer add a "+" sign to toggle call type. If your preferred call type is Sipdroid adding a + behind the number calls over Phone.

NOTE: Don't add anything to emergency numbers. They are always dialed over Phone.

![http://sipdroid.googlecode.com/svn/images/choose2.png](http://sipdroid.googlecode.com/svn/images/choose2.png)

### How can I dial a Skype ID? (Or any other SIP URI?) ###

#### From Contacts ####

When clicking on the "Chat" tab of a contact you get a menu like this:

![http://sipdroid.googlecode.com/svn/images/choose3.png](http://sipdroid.googlecode.com/svn/images/choose3.png)

Choosing Sipdroid makes a voice call to a PC over instant messaging.

Calling Skype users requires registering to PBXes. The callee needs to allow anonymous calls.

This also works for Google Talk, MSN, Yahoo, AIM, and ICQ users. All these recipients have to do is either invite user service@gtalk2voip.com (gtalk2voip@yahoo.com for Yahoo! Messenger) to his friend list, or submit his user id from [gtalk2voip main page](http://gtalk2voip.com/), to become reachable from Sipdroid.

If you want to call any other SIP URI add it to a contact as one of the two unsupported messengers, Jabber or QQ, and use above method to dial the SIP URI from contacts.

Note: PBXes only supports calling alphanumeric SIP URIs e.g. abc##@domain.tld. Calling URIs starting by a digit will result in a routing based on outbound dial rules.

#### From Sipdroid window ####

You can enter SIP URIs into the "Called Party Address" field in Sipdroid. For calling Skype users enter the Skype name followed by **@skype** into "Called Party Address". Calling Skype users requires registering to PBXes.

Note: PBXes only supports calling alphanumeric SIP URIs e.g. abc##@domain.tld. Calling URIs starting by a digit will result in a routing based on outbound dial rules.

### How are the buttons assigned? ###

Android reserves the red key for turning screen off and the green call button for answering a phone call. That's why they don't always work for Sipdroid, e.g. when screen is turned on the red key will first switch screen off, and then end call on another press.  The green button will not work for Sipdroid if there is a phone call ringing at the same time. In this case the green button will answer the GSM call.

That's why Sipdroid offers a sliding card. A call is off-hook if the card is at the top of the screen, and it is on-hook at the bottom. Just slide up to answer. Slide down to end call. If you want to reject an incoming call press the MENU button to select end call.

### How can I modify phone numbers on the fly? Where is the prefix option? ###

The _prefix_ option has been replaced by a more generic and flexible _search & replace_ feature. The "search & replace" option, available in **Advanced Options**, has the following form: `<search>,<replace>`

`<search>` is a [Java regular expression](http://java.sun.com/docs/books/tutorial/essential/regex/) with one or more [groups](http://java.sun.com/docs/books/tutorial/essential/regex/groups.html) which can be then use in `<replace>`

`<replace>` is a string with reference to group(s) from the `<search>` field.

If the regular expression is not valid or the format is wrong, the original number is used.

Examples:

| _Search & Replace_ | _Description_ |
|:-------------------|:--------------|
| `\+*1*(.*),1\1`    | fix for the common issue of contacts with or without 1 and +1 |
| `\+41(.*),0041\1`  | replace +41791111111 with 0041791111111 |
| `(.*),123\1`       | add 123 in front of the number (prefix) |
| `(.*),\1123`       | add 123 at the end of the number (postfix) |

### How do I exclude certain numbers from Sipdroid? ###

Choose **Advanced Options** and enter your pattern in the **exclude pattern** field.
Numbers can be exluded by type and/or number.
<br> Format is pattern,pattern,pattern...<br>
<br>
To exclude by <b>phone type</b> you can enter single or combination of the three supported types:<br>
<br>e.g. h,m,w or ho,mo,wo or home,mobile,work (excludes all home, mobile and work numbers)<br>
<br>
To exclude by <b>numbers</b> enter any java regular expression:<br>
<br>e.g. \A\+01 (excludes all numbers starting with +01).<br>
<br>
To exclude by <b>both</b> phone type and number:<br>
<br>e.g. m,1234 (exludes all mobile and numbers that contain 1234).<br>
<br>
<h3>What is "Trigger Callback/Callthru"?</h3>

Suppose you are outside your wireless LAN, or got a mobile Internet connection, but not good enough for a SIP call. Normally the dialer would fall back to Phone in this case.<br>
<br>
<ul><li>Enabling "trigger callback" will instead ask the PBX to initiate a callback to your mobile number, and connect the call to the dialed contact.<br>
<ul><li>This makes sense if you like the PBX features (like calling a SIP URI, simultaneous outbound, etc.), or if it's cheaper than a call from your mobile. I was using the function while roaming with a local SIM card. Some plans also allow you to get unlimited calls from a certain number. That number could be assigned to your PBX.</li></ul></li></ul>

<ul><li>Enabling "trigger callthru" will call a PBX's trunk/DID (or any other calling card platform), dial PIN & destination number as DTMF tones, and connect you.<br>
<ul><li>This is nice if you have unlimited minutes to a certain number or nationwide, and want to use them to dial out or dial internationally.</li></ul></li></ul>

Exclude pattern and search & replace get applied in the same way as for SIP calls.<br>
<br>
<h3>What types of video calls are supported?</h3>

There are three levels of operation for video calls.<br>
<br>
<h4>Sending</h4>
By pressing the MENU button and choosing "Send Video" you can start<br>
video transmission to a SIP phone with video.<br>
<br>
<h4>Receiving</h4>
This is not supported natively. If you are registered to PBXes and the<br>
other party starts sending video it will show up on the Android phone.<br>
<br>
<h4>Streaming</h4>
When you start sending video as described above while you are in a<br>
call to a regular phone, and you have a PBXes Premium Account, the<br>
other party can open your webcall URL, click on your photo and see<br>
your video.<br>
<br>
Streaming can also be used if you call somebody on his Android phone who is not registered to PBXes. Then he can still open your webcall URL from his mobile browser and see you.<br>
<br>
<h2>SIP Providers</h2>

<h3>What SIP providers is Sipdroid compatible with?</h3>

Sipdroid runs standard SIP. For full interoperability register Sipdroid to <a href='http://pbxes.org'>pbxes.org</a>. From there register your SIP accounts.<br>
<br>
Possible issues when registering directly to other SIP servers are:<br>
<br>
<ul><li>Battery drain on 3G/EDGE,<br>
</li><li>Unreliable incoming calls,<br>
</li><li>One way voice, or<br>
</li><li>No connection at all</li></ul>

<b>As you can see there is not just one issue. When Nokia released its SIP client in 2006 PBXes were the first to support it. It's a bunch of adjustments to account for phones that are not plugged into a single network, are battery powered and Java based. So unless you are a developer we don't recommend spending much time in getting your plain-vanilla Asterisk box suited for Sipdroid. Instead register your Asterisk to PBXes, too.</b>

For the future it is expected that SIP providers will become more interoperable (see also <a href='http://code.google.com/p/sipdroid/wiki/NewStandbyTechnique'>article</a>). As Sipdroid is a true open source project attracting many software developers, the application and its documentation will be updated as more information gets available.<br>
<br>
<h3>What advantages do I get by signing up for the Free Account at PBXes?</h3>

<ul><li>You can register several trunks to use multiple telephony service providers of your choice.<br>
</li><li><a href='http://pbxes.org'>pbxes.org</a> routes incoming calls over Sipdroid or Phone to you. If you are online you get them over VoIP, if off line you get them over GSM.</li></ul>

<h3>Which features are supported in Sipdroid?</h3>

Sipdroid presently supports basic call. All the typical PBX features are configured from the PC. This concept is much like the concept of Google's services that allow you e.g. to manage your calendar on the PC and access it remotely on your phone. The following features are provided by the Free Account on <a href='http://pbxes.org'>pbxes.org</a>:<br>
<br>
<ul><li>Change number format (e.g. convert the + codes)<br>
</li><li>Music on hold<br>
</li><li>Support of several modes for DTMF tones<br>
</li><li>Support for NAT (network address translation)<br>
</li><li>Simultaneous Outbound Calling<br>
</li><li>Screening anonymous callers</li></ul>

<img src='http://sipdroid.googlecode.com/svn/images/priv.png' />

<ul><li>Time-based routing for incoming calls<br>
</li><li>Attended Call Transfer<br>
</li><li>Conferences<br>
</li><li>Video Reception (Video Transmission is supported by Sipdroid natively)<br>
</li><li>Trigger callback or callthru (if no suitable data network available)<br>
</li><li>Calls to Skype users</li></ul>

You get even more <a href='http://pbxes.org/iptel_virtual-pbx.html'>features</a> on the paid accounts (e.g. Video Streaming, Announce Location, Call Recording, Improved Audio, Handoff of calls between networks).<br>
<br>
<h3>How can I set up PBXes?</h3>

Please have a look at the <a href='http://pbxes.org/community_e.php?display=wiki'>HELP section</a>. Under "Getting started" you find an introduction to the necessary steps.<br>
<br>
<b>It's all web based. No installation required.</b>

First you create extension(s) and trunk(s). Perform an echo test by dialing <code>*</code>43. Then you add at least one inbound and one outbound route. Leave the trunk name empty on your inbound route. The Android specific details can be found under "Mobile Extensions".<br>
<br>
The username to be entered in Sipdroid consists of account name, a dash ('-') and the extension number, e.g. "myuser-200". The password is that of the extension, not the password of your PBXes account.<br>
<br>
<h2>Android Applications</h2>

<h3>Ambient Light Sensor</h3>

This tool is recommended to save battery. It uses the camera to adjust screen brightness.<br>
<br>
<h3>Google Talk</h3>

See <a href='http://code.google.com/p/sipdroid/wiki/FAQ#How_can_I_dial_a_Skype_ID?_(Or_any_other_SIP_URI?)'>above</a>

<h3>GV</h3>

Sipdroid can be used to add true VoIP calling to the GV app. Both integrate amazingly well. Further info is available at <a href='http://iiordanov.blogspot.com/2009/07/sipdroid-gv-guava.html'>Iordans's blog</a>.<br>
<br>
<h3>Latitude, Weather Widgets, ...</h3>

We noticed that choppy voice on WLANs can be resolved by turning off permanent location updates. Alternatives are uploading position to PBXes and announcing it to contacts when they call you, and "Snowstorm weather widget" that allows you to set location manually.<br>
<br>
<h3>Netcounter</h3>

This is very nice to account your bandwidth usage on mobile networks. However, when you use WLANs only you should not install the present version. It wakes the device too often thus draining the battery.<br>
<br>
<h2>Hint for developer phones</h2>

One limitation has been noticed on Android developer phones (ADP1). Due to limited memory home screen often takes several seconds to load. Luckily these phones allow root access. Issue the command "echo ro.HOME_APP_ADJ=1 >/data/local.prop" and reboot, to lock home screen in memory.