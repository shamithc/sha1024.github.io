---
title: "How to measure Availability"
date: 2024-02-14T09:06:41+05:30
---


## Availabilty

High availability is a critical component in building a highly scalable system.

### What is Availabilty?

System to be Operational when required to perform operations. 

> Let take an exampe, 
In a payment system, high availability is essential as it ensures that the system is always operational and able to process transactions whenever a user needs to make a payment. Any downtime or system failures can result in lost revenue, unhappy customers, and damage to the reputation of the payment provider. Therefore, ensuring that the payment system is highly available is crucial for its success.


#### How to Measure Availabilty?

Measuring availabilty is important in designing highly available system. As a enginer, you can understand performance of thea pplication only if meauring the availabilty of the system. Common mechanism to measure the availablity is perectange of time system is accessible 

```
System availabilty percentage = (Total time - Total down time)/Total time
```

Let's consider an example, in January, the system was down for 50 minutes and 5 minutes. What is the availability of the system?

```
Total number of seconds in a month = (31 days* 24hours * 60 minutes * 60 Seconds) = 2678400 seconds
Total number of  seconds down = (50 minutes + 5 minutes) * 60 = 3300 seconds

Site availabilty percentage = (2678400 - 3300)/2678400 = 0.998767921 * 100 = 99.8767921 %
```

I hope you see availability is expressed in the form of "the nines". You can see below table below. A System of 2 nine availability means that the system was available 99% of the time and had downtime for 432 minutes. In the above example, availability is mentioned as 3 nines **(99.8767921% compared to 99.9 %)**.


|      Nines     |Percentage                     |Monthly Outage               |
|----------------|-------------------------------|-----------------------------|
|2 nines         |99%                            |432 minutes                  |
|3 nines         |99.9%                          |43 minutes                   |
|4 nines         |99.99%                         |4 minutes                    |
|5 nines         |99.999%                        |26 seconds                   |
|6 nines         |99.9999%                       |2.6 seconds                  |