### Let's talk about apps.

Why do you need to know about apps? I suppose you're curious. How do those apps, those circles on your cell phone, work? Well, this is the lecture where we're gonna explain how they work.

#### The Three Types of Cell Phone Apps

What are they? There are **native** apps, **web** apps, and **hybrid** apps.

So those little circles on your cell phone that you're looking at can be either a native app, a web app, or a hybrid app.

#### Native Apps

A native app runs on an operating system. And you may say, "Well, what am I talking about here, operating system?"

An operating system is what makes your hardware work. For example, if you have a cell phone, that's just a piece of hardware. You can't turn it on; you can't do anything with it.

You have a computer, just a piece of hardware. You can't do anything with it either.

So what makes it work?

Well, between you and the hardware (for example, a cell phone or a computer), what gets between you and the hardware is the operating system.

Okay, so this hardware is dead without the operating system, and the operating system is dead without you using it.

So this operating system is kind of like the middleman between you and the hardware.

It's what makes the hardware work because a cell phone by itself, without an operating system, is useless.

A computer without an operating system is also useless.

Once you put the operating system in the hardware, then it becomes what? An operating system.

That's why they call it an "operating system."

#### Common Operating Systems

Now, what are the most common operating systems?

The most common operating systems are:

- **Windows**  
- **Mac OSX**: meaning the Apple operating system. This X means version 10. Once it got to version 10, they started calling it Mac Operating System X, for 10.
- **Linux**: another operating system used primarily for servers and big computations, not for personal computers.

Now, there are also cell phone operating systems. 

#### Cell Phone Operating Systems

Examples include:

- **Android**
- **iOS**: which is the Apple iPhone operating system. They used to call it the iPhone operating system, but now they just call it iOS for short.

There are more operating systems out there, such as Blackberry, but who has a Blackberry anymore?

And Microsoft? Who's using a Microsoft operating system on a cell phone?

If you put the Windows operating system on a computer, it looks like a Windows computer.

If you put Mac OS on a computer, it looks like an Apple computer.

If you put Android on a cell phone, it looks like an Android phone.

If you put iOS on a cell phone, it looks like an Apple iPhone.

#### APIs on Operating Systems

Each operating system has APIs on it.

Maybe you don't realize this, but it has APIs.

For example, on your cell phone:

- **Vibrating**
- **Microphone**
- **Camera**
- **Location**
- **Calls**
- **Speaker**
- **Touch screen**
- **Keyboard**

These are low-level APIs, that is, very simple APIs.

#### High-Level APIs

In addition to these generally hardware APIs, you also have what's called high-level APIs.

These are a bit more complicated, such as:

- **Calendar**
- **Push notifications**
- **Browser**
- **Email**
- **Contacts**

In general, you can't remove these APIs.

For example, if you remove the location API, you won't be able to use the API to find out your location, and you won't be able to use Waze or Google Maps.

So, operating systems have all these APIs that apps can call to make use of your device’s hardware and other functionalities.

Now that we understand what an operating system is, let's go back to the explanation of what a native app is.

#### Native Apps

You have your cell phone operating system. This operating system could be Android, or it could be iOS, and in this operating system are APIs. The native app calls the APIs in the operating system; it has direct access to the operating system APIs. Therefore, your native app has to be specific to the operating system.

If you're gonna create an app for Android, say the operating system is Android, then this has to be an Android native app. You also have to create the same app, an iOS app, where this is Android, to access an iOS operating system.

If you're creating an Android app, then you install it, in general, using Google Play, and if you create an iOS app, you install it, generally, using Apple Play Store. This is why, when you download this app, it generally says install on Google Play or install on App Store.

Examples of native apps include Waze, Twitter, Google Maps, Google Translate.

Say for example, we want to use the Google Waze app. Well how does that work? Well the Google Waze app is going to call the location API, right, and when it calls the location API, it gets back the location. It then sends a message over to a Waze computer somewhere which calculates directions and comes back with directions.

#### Web Apps

Now a web app does not run directly on the operating system; it runs in a browser. So you have the browser, and in the browser is the app. The browser itself is an API, just like the app is an API. So it is limited to what APIs the browser can call. You don't have a browser being able to call the camera.

Examples of web APIs include Google, YouTube, Wikipedia. So if you wanna see these types of APIs downloaded on your cell phone, and you'll see examples of web apps.

Now when you look at them, they're gonna look just like webpages because they're made using HTML and maybe also CSS and JavaScript but must have HTML. HTML is what's used to render webpages or to make webpages show.

You only have to design the web app once because HTML can work in any browser. HTML can work in the Chrome browser, can work in the Firefox browser, can work in the Internet Explorer browser, can work in the Postman browser. So you just design it once, and you use the browser to call the operating system APIs.

That's one of the benefits of web apps is that you only have to design it once; you don't have to design it for each operating system.

Now they've come out with HTML5, which provides you with more capabilities. You can do more things in the app. You don't have to depend on the browser. For example, you can use audio; you can use video; you can use your location. Because it's HTML5, it's providing more capability than just the browser.

#### Hybrid Apps

Now the third type of app is what's called a hybrid app, and you can guess what this is. This has a hybrid of both the web app and the native app. It has aspects of both, which makes it a hybrid.

Examples of hybrid apps include Bank of America and Facebook. So try downloading those on your cell phone to see what hybrid apps look like.

Sometimes it looks like a native app; sometimes it looks like a web app, in other words, a webpage.

There are generally two ways that hybrid apps work.

In the first way, you have the browser, cell phone browser, and the web app in the browser, and the browser calls the API in the operating system, right? This is the same as a web app. But you also have the capability of a native app, which directly calls the API in the operating system. And these can talk to each other.

In the second way, you have a web app that is an app located in a browser. You have the operating system and the APIs in the operating system. And then you have what's called middleware, where the app calls the browser, which calls the middleware, which calls the operating system API. So you have access to all the APIs through the middleware.

#### Comparison Between Native, Web, and Hybrid Apps

Now we know the three cell phone app types: native, hybrid, and web. Let's do a comparison between all three of them.

**Best Quality:** The best quality app is definitely native. That has the best performance. People who use native apps love it.

**Best Speed:** The native app has the best speed because it has direct access to the operating system. There's no browser that it has to go through to get to the operating system APIs.

**Least Cost:** The least cost is definitely the web app, and the reason why is because you just have to create it once. You just have to use HTML. You don't have to worry about the operating system because the browser will access the operating system.

The ability to download on Google Play or App Store, you can do that for native or for hybrid.

And as far as device access, the APIs on the operating system, well definitely the native app is best for that because it has access to all the APIs, and the hybrid app has access to some of the APIs.

#### Should I choose native, hybrid, or web?

Well it depends on your situation. If say you're a big company that's gonna have a ton of downloads of apps, for example, the Google Translate app is used all over the world, there's gonna be hundreds of thousands of people, maybe millions of people downloading that app, then you want to create the native app because that has the best quality.

The problem with native apps is that it costs a lot, not only in terms of money, but also in terms of time—140,000 dollars, a team of developers, over four months to create a basic native app.

The hybrid app can be kind of buggy and kinda slow, but it's an option because it costs less time and effort as the native app.

The web app is the easiest way of creating apps. So if you're just starting out,

 if you're just by yourself, create a web app. Now your app is gonna look like a webpage because you're using HTML, but the way things are headed, web and hybrid apps are becoming closer to native apps as far as power.

For example, the web app now has HTML5 capability, which provides you with more capabilities than just creating a webpage.

So unless you're a big company with lots of money, or you're interested in creating the best quality API, then choose a web app.

Another problem with apps is that people are reluctant to download apps. You may have been in a situation where your cell phone asks you to download an app. Do you want to download this app? You said no, which is heartbreaking to the person who created a beautiful native app, spent say $200,000, half-a-year on it, and you just say, "Hey, I don't want to download it," because you get enough apps already on your cell phone, and you don't want any more; you're busy.

Thanks for watching this lecture on cell phone apps. Hopefully, now you have a better idea of how they work.
