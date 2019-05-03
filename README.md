Real Time Event Decisioning
===========================

With the ever growing number of channels of communications, customer interactions becomes a rather complex problem to solve. Maintaining a consistent 360 degree view of the customer is very important. With Customers making use of digital channels for communication with the banks, it is very important for the banks to make to distance doesnt discount on the personalized banking experience that the customer deserves. As is rightly said, “Automate the processes, not the interaction”. The following model shows how we can create a tailored experience for the customer at scale.

Architecture
=============

![Architecture](https://github.com/snandakumar87/event-analysis-openshift-provision/blob/master/docs:images/Architecture.png)

  * Mock Emitter: This simulates the customer events (reflection of customer’s interaction with the Bank)
AMQ Streams: Helps support event streaming.

  * KStreams: the light-weight library provides event processing capabilities, and encapsulates the Java API call to the Rules Engine for processing.

  * Red Hat Decision Manager: Provides for the heart of the decisioning logic. Filters useful events and predict the next best action.

  * Nexus Repository: Remote maven repo to house the decision packages authored using the Decision Central environment.

  * Vertx Kafka Client: Provides for a simulation of downstream systems.

All of the components run on Red Hat Openshift.


The event decisioning makes use of the Customer Profile data and the Event information to fire appropriate rules.
![eventdecisions](https://github.com/snandakumar87/event-analysis-openshift-provision/blob/master/docs:images/Decisions.png)


Scenario walkthrough
====================

John makes an airline purchase on the credit card and he has an Offer upgrade privilege flag associated with him. (This flag denotes the customer’s history, this can be a big data analytical model or a look up based on disparate data sources)

![scenario1](https://github.com/snandakumar87/event-analysis-openshift-provision/blob/master/docs:images/Scenario1.jpg)

"John" {"eventCategory": "CC_TRANSACTION", "eventValue": "AIRLINE_PURCHASE", "eventSource": "WEBSITE"}'

The following Offer is sent to the user.

“Upgrade to Gold Premium Card today and enjoy airline benefits”

![scenario1](https://github.com/snandakumar87/event-analysis-openshift-provision/blob/master/docs:images/customerlogin.png)

Similarly down stream systems can extend this data and create meaningful dashboards and functionality on top of the filtered events.

Refer to the following for detailed Demo setup, walthrough and more scenarios.

[Real Time Event Decisions](https://docs.google.com/document/d/1NoQHsm-2UooBUXYzAbrir-qvZwj-1DrQCp2BZ9vCn54/edit?usp=sharing) 




