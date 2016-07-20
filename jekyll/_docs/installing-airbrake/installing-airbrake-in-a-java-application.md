---
layout: classic-docs
title: Installing Airbrake in a Java application
short-title: Java
categories: [installing-airbrake]
last_updated: May 11, 2016
description: Installing Airbrake in a Java application
---

![java flag](/docs/assets/img/docs/java_flag.jpeg)

Configuring Airbrake is a simple task whether you are a Java Novice or Expert.
In our examples we show you how to configure it with Maven and without it. If
you identify bugs or would like to suggest a feature please refer to
[Airbrake-java](https://github.com/airbrake/airbrake-java) on Github.

### [Maven](http://maven.apache.org): Project management/workflow tool
- If you want to bundle your dependencies into a WAR or EAR file, set the
  packaging type of your project to EAR or WAR.
- If you want a JAR file that includes your code and dependencies "All-In-One",
  use the assembly plugin with the jar-with-dependencies descriptor.
- If you want to pull your dependencies into the target directory
  interactively, use the dependency plugin to copy your files in.

### [log4j (v1)](http://logging.apache.org/log4j/1.2/): Feature rich logging utility
- You have the ability to set logging parameters in the config file, rather
  than recompiling
- You can configure the format that logs are written in (text, html, SMTP
  headers, etc..)
- You can filter results by the severity:
  - DEBUG : low level detailed info such as cache hit/miss, DB connections
  - INFO : coarse info such as progress or state of current action
  - WARN : unexpected events but more than likely won't halt the application
  - ERROR : unexpected but serious event, unstable app state

# Project 1: Airbrake, Maven, and log4j

**Config file pom.xml, packaging dependencies in one JAR**

{% highlight xml %}
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.mycompany.app</groupId>
  <artifactId>my-app</artifactId>
  <packaging>jar</packaging>
  <version>1.0</version>
  <name>my-app</name>
  <url>http://maven.apache.org</url>
  <dependencies>
    <dependency>
      <groupId>log4j</groupId>
      <artifactId>log4j</artifactId>
      <version>1.2.17</version>
    </dependency>
    <dependency>
      <groupId>io.airbrake</groupId>
      <artifactId>airbrake-java</artifactId>
      <version>2.2.8</version>
    </dependency>
  </dependencies>
  <build>
    <plugins>
      <plugin>
        <artifactId>maven-assembly-plugin</artifactId>
        <configuration>
          <archive>
            <manifest>
              <mainClass>fully.qualified.MainClass</mainClass>
            </manifest>
          </archive>
          <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
          </descriptorRefs>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
{% endhighlight %}

### Config file for log4j.properties
place anywhere in your project's Class path

{% highlight java %}
log4j.rootLogger=INFO, stdout, airbrake

log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=[%d,%p] [%c{1}.%M:%L] %m%n

log4j.appender.airbrake=airbrake.AirbrakeAppender
log4j.appender.airbrake.api_key=YOUR_KEY_HERE
log4j.appender.airbrake.env=development
// log4j.appender.airbrake.env=production
// log4j.appender.airbrake.env=test
log4j.appender.airbrake.enabled=true
log4j.appender.airbrake.url=http://api.airbrake.io/notifier_api/v2/notices
{% endhighlight %}

**Simple Java app with an exception:**

{% highlight java %}
package com.mycompany.app;
import org.apache.log4j.*;

public class App {
  private static final Logger logger = Logger.getLogger(App.class);
  public static void main(String args[]) {
    try {
      int a[] = new int[2];
      System.out.println("Access element three :" + a[3]);
    }
    catch(ArrayIndexOutOfBoundsException e) {
      System.out.println("Exception thrown  :" + e);
      logger.error(e);
    }
    System.out.println("Out of the block");
  }
}
{% endhighlight %}

**Build App:**

{% highlight bash %}
mvn clean compile assembly:single -e -X -l build.log
{% endhighlight %}

# Project 2: Using Airbrake without Maven

Ensure you add the [Airbrake jar](https://github.com/airbrake/airbrake-java/blob/master/maven2/io/airbrake/airbrake-java/2.2.8/airbrake-java-2.2.8.jar?raw=true)
to your classpath

### Simple Java app with an exception

{% highlight java %}
import airbrake.*;

public class App {
  public static void main(String args[]) {
    try {
      int a[] = new int[2];
      System.out.println("Access element four :" + a[4]);
    }
    catch(ArrayIndexOutOfBoundsException e) {
      AirbrakeNotice notice = new AirbrakeNoticeBuilder("YOUR_KEY_HERE", e, "env") {
        {
          // Add custom parameters to your exceptions
          addSessionKey("myCustomParam", myCustomParam);
        }
      }.newNotice();
      AirbrakeNotifier notifier = new AirbrakeNotifier();
      notifier.notify(notice);
      System.out.println("Exception thrown  :" + e);
    }
    System.out.println("Out of the block");
  }
}
{% endhighlight %}

# Advanced configuration options

## Sending uncaught exceptions to Airbrake
You can send uncaught exceptions in your application to Airbrake using
`setUncaughtExceptionHandler`.  Here's an example:

{% highlight java %}
Thread.currentThread().setUncaughtExceptionHandler(new Thread.UncaughtExceptionHandler() {
  public void uncaughtException(Thread t, Throwable e) {
    logger.error(e);
  }
});
{% endhighlight %}

## Filtering uncaught exceptions
Using the last example, we can also filter exceptions by class.  Say for
example, that you'd like to filter out any exceptions of class
`NullPointerException`, then you can add a simple if statement as shown here:

{% highlight java %}
Thread.currentThread().setUncaughtExceptionHandler(new Thread.UncaughtExceptionHandler() {
  public void uncaughtException(Thread t, Throwable e) {
    if (e instanceof NullPointerException) {
      System.out.println("Uncaught exception ignored");
      return;
    }
    logger.error(e);
  }
});
{% endhighlight %}
