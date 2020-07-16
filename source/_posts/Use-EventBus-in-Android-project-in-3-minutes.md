---
title: Use EventBus in Android project in 3 minutes
date: 2020-07-15 15:20:39
categories: engineer
tags:
- Android
---

## What is EventBus

> EventBus is an open-source library for Android and Java using the publisher/subscriber pattern for loose coupling. EventBus enables central communication to decoupled classes with just a few lines of code – simplifying the code, removing dependencies, and speeding up app development.

Simply speaking, EventBus is a "bus" to enable your application's codes to "notify" other codes when something happens.

With EventBus, you can:

* simplifies the communication between components
* decouples event senders and receivers
* performs well with UI artifacts (e.g. Activities, Fragments) and background threads
* avoids complex and error-prone dependencies and life cycle issues
* is fast; specifically optimized for high performance
* is tiny (~60k jar)
* is proven in practice by apps with 1,000,000,000+ installs
* has advanced features like delivery threads, subscriber priorities, etc.

## How to use EventBus in your project

### Define an Event

Events are POJO (plain old Java object) without any specific requirements, you can define a simple class within one minute.

```java
// This could be placed in anywhere in your project.
public class MyEvent {
    public final int eventType;
    public MyEvent(int eventType) {
        this.eventType = eventType;
    }
}
```

### Post an Event

Use the following code in where you want to post an event().

```java
// This could be in, forexample, onCreate method for some Activities.
EventBus.getDefault().post(new MyEvent(1));
```

### Set Subscribers

Subscribers also need to **register** themselves to **and unregister** from the bus. Only while subscribers are registered, they will receive events. In Android, in activities and fragments you should usually register [according to their life cycle](https://developer.android.com/guide/components/activities/activity-lifecycle.html). For most cases onStart/onStop works fine:

```java
@Override
public void onStart() {
    super.onStart();
    EventBus.getDefault().register(this);
}
 
@Override
public void onStop() {
    EventBus.getDefault().unregister(this);
    super.onStop();
}

// This method will be called when a MyEvent is posted
@Subscribe
public void onMessageEvent(MyEvent event) {
		if(event.eventType == 1){
				// do something on event
		}
}
```

