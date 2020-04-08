# Research

## Mobile App Platform

Since the opening of Apple App Store in 2008, the number of mobile applications has reached more than 2 million on both Android and iOS platforms in more than a decade. Today, urbanites use their mobile phones to access the Internet every fat to do a variety of things, including online financial management, Instagram and trading. Some people can forget to take their wallets out of the street, but they can't go out without their smart phones. 

The development of mobile applications is also all the rage. To this day, mobile application development has gradually evolved into different types, and companies can choose the type of development suitable for the enterprise's mobile application according to their needs, resources, development time, and so on.

### Native App

Native app means develop an application using the native programming language of the mobile system. From the earliest ObjectiveC to Swift for iOS, or Java to Kotlin for Android, are the most direct development methods. In theory, native applications should be able to make the most of all the capabilities of the phone and achieve the best user experience.

Native applications can change immediately following the upgrade of the mobile phone system, so it can make fuller use of the functions of the phone than other development types of applications. For example, machine learning, or Augmented Reality, epoch has been quite popular in recent years, is a native application that can be used for the first time.

In contrast, the disadvantage of native applications is that the development cost is relatively high. In the iOS or Android market, sometimes even PC users need to taken into account. Unless under special requirements, it is basically necessary to support users on more than two platforms at the same time. With multiple platforms being developed separately, it is not uncommon to double the cost and time of development.

### Hybrid App / Cross-platform App

When the problems of time and development cost of native applications become more and more obvious, the market naturally has relative solutions at the historic moment, and this is the hybrid application.

The basic concept of a hybrid application is to place a web browser in the smart phone. Through this browser, you can open a website that simulates a mobile phone application. Because browsers are common to mobile phones, all programs that can be shared are presented in the form of web pages. For the functions that the web page fails to implement, it will implement by native programming language. Taking the application of Android and iOS platforms as an example, a hybrid application can achieve twice the development cost and time of a native application by about 1.5 times the development cost and time.

In 2015, Ionic, which used AngularJS and Cordova as its foundation, was a madman, and a large number of applications written in Ionic emerged. However, the core problem of the hybrid application at that time was the performance of the user interface performance. At the time, the browser performance of Android and iOS was very limited. In terms of user experience, hybrid applications were much worse than native applications.

In order to reduce development costs without giving up the user experience, various mobile application companies continue to explore, of which Cross-platform App is the successor of hybrid applications. The biggest difference from hybrid applications is that they improve the improve the user interface experience. Instead of using web pages and browsers, they provide a common user interface development framework for developers to develop native user interfaces. This greatly improves the user experience of hybrid applications. Facebook's React Native, Microsofts's Xamarin, Google's Flutter or Vue Native, these are cross-platform application development,ent frameworks.

However, although these development frameworks all claim to be development tools for native applications, they are quite similar to native applications in terms of user experience and performance. But cross-platform applications often take at least a few months to support the latest smart phone features, which is always not as fast as native applications. Even so, cross-platform applications can still meet the needs of more than 90% of users. Mobile applications that you often come across, including Instagram, Evernote, UBER, Twitter, Netflix, etc., are all cross-platform applications, which shows that cross-platform applications have become the mainstream of today's development model.

#### Xamarin
Xamarin was born in 2011. The first set of products was Xamarin.Mac in 2012. iOS apps can be developed using C# language and successfully listed on Apple's App Store. Xamarin was bought and integrated by Microsoft shortly thereafter. In Visual Studio, the use of Xamarin to develop App in the past required additional payment, but now as long as you download Visual Studio Community, you can directly develop Xamarin related applications.

The main feature of Xamarin is that developers can directly use C# to call APIs of Android and iOS to generate a native interface. The architecture is basically very similar to the native language architecture (Android, iOS). The development is almost the same. The advantage of using Xamarin to develop cross-platform apps is that the general logic program can be used directly between the two projects of Xamarin.Android or Xamarin.iOS. But we still have to call the respective underlying API if it need to render the UI part. In other words, Xamarin only unified the development language, in fact, you must still understand some Android and iOS development frameworks to develop.

Form the perspective of Github's community thermal network, although Xamarin has launched products as early as 2011, the thermal network between developers seems to be not high, because Xamarin uses the underlying API to present the UI, so the screen presentation between different devices can sometimes be very different, for example, TabbedPage is very different devices can sometimes be very different, for example, TabbedPage is very different on Android and iOS.

In addition, Xamarin's Hot Reload can only be used to render XAML UI. Although ut supports fast deployment, it still seems to require a long compiling time.

Based on the above conclusions, developers who are more suitable to use Xamarin as a development tool should be:

1. Have C# development experience
2. Developers accustomed to the Visual Studio development language as the main development tool
3. Developers who have a certain understanding of the Android or iOS UI layer framework
4. Newcomers who want to quickly develop a simple business process App

#### React Native

React Native is a cross-platform development framework that Facebook opened its source code in May 2014. The development language is Javascript. The syntax and architecture are very similar to the front-end web development React.JS JSX and CSS. It allows front-end web developers to quickly enter the development area of React Native App.

The framework of the React Native operation is built with Javascript. Javascript can directly call Native to build the UI. In addition, React Native also supports real-time hot reload. In other words, React Native does not need to be re-run during the Run-time stage. Compiling programs can directly control the control operations of the UI or program logic, and the execution performance is also very close to the Native development performance.

Observed by the popularity of the community, React Native can be regarded as a very fast and popular development framework in recent years. The main reason should be attributed to the success of the React.JS development model. Many React.JS front-end web developers can quickly enter the ranks of mobile device application development. In addition, Facebook and Instagram apps are also developed using React Native. I believe that many players who are curious about the function of Facebook to update components locally should want to understand how Native React it works, but React Native uses Bridge to call the underlying Native UI  through Javascript after all, so the consistency of the UI appearance of different operating systems depends on the third-party components.

However, taking Tabbled Page as an example, compared to Xamarin.Form, React Native's Tanned Page has made it possible for the display of operating system screens of different platforms to be quite similar.

Relatively speaking, the React Native framework is very suitable for developers using these conditions:

1. Those who only understand Web front-end development technology, because they only need to understand Javascript and CSS to understand React Native code.
2. Developers who like React.JS development architecture
3. Developers who need to develop cross-platform apps quickly

#### Flutter

Flutter was announced by Google at the 2015 Flutter conference. The official stable version was announced on December 4, 2018. The bottom layer mainly uses C++ for development to connect iOS and Android, and uses Google's Skia graphics library to provide the bottom graphic support. All of Flutter's UI is composed by combining various Widge. The basic library is written by Dart, which provides the categories and libraries required by Flutter.

Flutter's hot reload can inject the modifications from original file into the running application. Flutter expands this function by supporting stateful hot reload. In most cases, changes to the source code can be immediately reflected in the executed application without restarting or losing any state.

Different from the way that Xamarin and React Native call the native interface, the biggest difference of Flutter is that the interface of Flutter is derived through the 2D engine Skia Render, so the performance is even better than the native application. Because all the UI is rendered, the screen output by Flutter are almost the same on iOS and Android.

Judging from the popularity of the community, Flutter has grown faster than React Native. According to the number of followers on Github, it has already surpassed React Native. It should be expected to become the most popular cross-platform development tool.

However, compared with Xamarin and React Native, the stable version of Flutter has only been released to the present in the past year or so. The stability of the framework has yet to be tested by time. The method of direct rendering is likely to replace the original development framework that use Native UI, and become a new generation of popular cross-platform device development trend.

Flutter has a high consistency on the screens presented on different devices, and developers can reduce many maintenance costs arising from the inconsistency of output functions.

What types of developers is Flutter suitable for:

1. Requires consistency in screen display across platforms
2. The product needs to be online in the fastest time
3. Those with higher UI performance requirements

### Web App / Progressive Web Application

To put it plainly, the Web App is just a web page, but this kind of web page is mostly built using the framework of Single page Applications. With the development of browsers on mobile phones in recent years, web apps have been able to give users the feeling of being very close to native applications.

In terms of performance, the performance of web apps in current browsers has improved a lot compared to a few years ago, but of course it is inferior to the two mentioned above. In terms of functions, the web app also has many functions that cannot be achieved, such as reading QR Code, Bluetooth device information, etc., and cannot use paid functions such as Apple Store or Play Store. However, if the enterprise's application is mainly based on simple data such as text and pictures like a shopping network, the web app is definitely a good choice.

Base on the advantages of web apps, iOS and Android also made corresponding performance enhancements, so Progressive Web App appeared. When you use Safari on iOS or Chrome on Android to browse the web, users can choose to add the web page to the desktop of the phone, so that the web page will appear as a mobile application, for the average user, PWA looks no different from other mobile applications. And these applications can also use the functions that many native applications have, such as pushing information, reading coordinates, taking pictures with the camera, using the mobile phone compass, and so on.

Web app and Progressive Web Application also have a very prominent advantage, that is, it can be used directly without downloading through the App Store. There are many reasons why users refuse to download native apps, such as limited Internet data, insufficient phone capacity, and too many apps installed on their phones. The web app and PWA are to dispel the concerns of these users. Users can simply scan the QR Code or search on Google to start using it. This fast experience is quite effective for promoting new products.

The most important thing is that the development cost and time of the web application is the shortest among various development models. With the lowest cost, it can support almost all mobile phone platforms, even computer desktops can be used simultaneously. It is very suitable for some such as online shopping, it is a service that does not require many functions of the mobile phone to reserve a room, etc..

## Ecommerce Platform

### Magento

Magento is an open source e-commerce platform written in PHP programming language; it is mainly for enterprise-level applications and can handle various needs.

The technical requirements of Magento's website construction are relatively high, and the cost of operation and maintenance is relatively large, so Magento is suitable for enterprises with many types of SKUs, large traffic, and high investment. The large traffic is because some e-commerce systems like Opencart, the system performance will be reduced when the traffic is large, and Magento will be more stable.

Magento is designed to be very flexible, with a modular architecture system and rich functions, which is easy to integrate seamlessly with third-party applications. Since magento is open source, the code is completely in your own hands, so you can personalize all the content of the website according to your needs, including Shopping flow, page content, custom buyer show, reviews, etc. can think of everything. Thousands of special function plug-ins for Magento have been developed by global enthusiasts and enterprises, which can be turned on and off at any time after installation. In addition, Magento does not have any platform commissions. The server, source code, and database are owned by the business owner.