+++
language = "en"
tags = [
]
date = "2018-09-26T15:44:52-05:00"
type = "single"
nobc = true
+++

## The Domain

This is the documentation repository for development of some services that use Short Burst Data (SBD) over the Iridium satellite network.

### Motivation

The initial sponsor of this work is the Canadian Department of Fisheries and Oceans (DFO). As part of their modernization of systems to provide sustainable fisheries and protect ecosystems, some remote communication needs are required for

- Timely reporting and data capture from remote areas, including offshore.
- Providing notices to fishermen and other mariners in remote areas.

The successful deployment of Iridium NEXT has made sustainable, a global satellite coverage that is aiming to grow into many new applications beyond "phone calls".  A current capability is a Short Burst Data, SBD, service that is similar to the Short Message Service, SMS, that is commonly used in cellular networks.

Just as many services are implemented using the SMS messages, now these kinds of applications can be accessed anywhere over SBD. The design key is to keep the messages short.

For familiarity with Iridium see the [Iridium references](references/iridium/)

### Services

As this project aims to implement services, it is best to use an Iridium Value Added Reseller (VAR). There will likely be many VAR offering in the future as the new capabilities of Iridium NEXT are enabled.

For the service deployment we need a terminal for the remote user and a network capability that links the messages to a Network/Cloud based application that we will implement.

There are established VARs with terminals and service packages that we can use.

#### Rock Seven Mobile Services Ltd

[Rock Seven](http://rock7mobile.com) is an established supporter of application builders and has evolved SBD service packages and terminals that are designed for ocean use already.  One is [RockSTAR](http://rock7mobile.com/products-rockstar) which we will use initially to prototype the applications that we decide to build.

#### Garmin

Garmin has purchased DeLorme that built an Iridium terminal, [InReach Explorer](https://buy.garmin.com/en-CA/CA/p/561269#overview). It is best for land based value due to maps integration and is not quite as waterproof as the RockSTAR.

### Applications

The architecture of these SBD services is all very similar with the differences at the user end/phone/terminal where the data entry and alert viewing is presented. There are similar difference at the network end of the application where the information is recorded.

This project will focus on a few applications to prove the value of SBD. Here are a few that we have studied to act a user needs and domain driven design areas.

#### Fish Catch Reporting

This will be for offshore use.  The intent is to do timely data entry in the remote area.

#### Notices of fishery closures

Some notices are time critical, in the case that a fishery has to be closed due to an unplanned risk to health. The location of the satellite receivers can be used to focus the delivery of the notifications.

#### Report of Whales in a ship traffic area

The location of Whales can be reported quickly with their approximate location.  The notices could be focussed to the ships in the vicinity in case a lower speed of travel is  required.


### Technologies

This section will summarize the technology components used in the Application implementations.  

#### RockSTAR SBD device

One of the end-user terminals used for the SBD connection. There is a companion app for iPhone, R7 Connect.

#### Vapor Web Server

Vapor is a modern web server technology that is suited to build applications that will handle the reports and interface to other DFO systems. The conversions of the SBD messages and the interfaces and information systems where the application input needs to be stored.

#### iPhone user device

The satellite terminal, RockSTAR,  has buttons optimized to trigger special alerts and is not an ideal device to enter messages.  To make message entry easier, the SBD terminal vendors have a companion iPhone App that can be used to offer a messaging interface and relay it using Bluetooth to the SBD terminal for sending.

An option exists to send the application reports over the cellular/wifi networks if the are in range and to only use the SBD messages when necessary.

#### Custom iPhone App

To optimize the user interface for the Applications it would be done from a simple App to make custom user presentation and for data input. Ideally this custom app can communicate to the RockSTAR app, R7 Connect.