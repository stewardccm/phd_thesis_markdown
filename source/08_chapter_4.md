# Design of the solution

As mentioned above, the core problem that I want to solve would be the very good works from our fresh designer are buried and do not have chance to let others know. This problem is mainly caused by designers need to have a many connections before they can built up their own brands. However, the fresh designers may not have the chances or platforms to know more people and get resources to promote their well products to other places. If there is a platform that provide a chances to let them promote their products and learn more built up skills for their further usage.

By finding the suitable solution of this project, I have studied a similar cases done by Hong Kong Polytechnic University.

For the platform which is ITC Store and is done by Hong Kong Polytechnic University, it is found the their platform has some benefits and disadvantages that fulfil the need of this project.

The benefits:

- Connect with the offline store, the customer can be take a look of the product before they buy from web store
- Provide a online store for other counties have a way to know more our local designer products
- There has a middleman to monitor the uploaded information

The disadvantages:

- Designers don't have any control of there products on the website
- There do not provide any data analyse service to the designers
- Customers need to contact to the designer though the middleman, it take time for the communication

It is found out the studied case neither solve the problems in Hong Kong, thus we need to come up the following solutions to solve the problems.

As the problem of designers don't have any control of their products on the website, I would build up a web store with a backend system and mobile application for designers to upload the products and have different settings.

As the problem of lacking contact to the designer, customers can contact the designer though chat room from the web store. The web store and mobile app can show the newest product from the local designers. All the sales data will upload to the server and database for further analysis which provide to the designers.

After doing the research, the React Native in cross-platform application is the most suitable for this project to complete in a short periods.

## Development Difficulties

Since the project time period limitation and the requirement of the CST student, the mainly development in this project will more force on how to use a cross-platform language can be use to built a native like mobile application that can function on both iOS and Android system. Therefore, the web store with Mangeto is only have the basic function that provided by the framework and the development of the mobile application for designers is cut off.

In addition, the version of the React Native I used is the latest version. However, some of the plugins are not yet support the latest one, like use Apple Pay / Google Pay for in-store purchase, therefore it cannot be provided in this demo. 

Lastly, the image recognition function need a huge library which have trained. During to the time limited,  MobileNet pre-trained model is used for the image recognition. The data which the model provided is not what this project need, therefore it is only for demo usage only.

## UI Design

### Mobile Platform

#### Connected with Magento API

![Index Page \label{ref_a_figure}](source/figures/01.png){ width=50% }

![Product Detail \label{ref_a_figure}](source/figures/02.png){ width=50% }

![Explore \label{ref_a_figure}](source/figures/03.png){ width=50% }

![Login \label{ref_a_figure}](source/figures/04.png){ width=50% }

#### Withoutconnect Magento API

![Index Page \label{ref_a_figure}](source/figures/05.png){ width=50% }

![Catalog \label{ref_a_figure}](source/figures/06.png){ width=50% }

![Product Detail \label{ref_a_figure}](source/figures/07.png){ width=50% }

![Search \label{ref_a_figure}](source/figures/08.png){ width=50% }

### Web Platform

![Index Page \label{ref_a_figure}](source/figures/09.jpg){ width=50% }

![Product Detail \label{ref_a_figure}](source/figures/10.jpg){ width=50% }

![Checkout \label{ref_a_figure}](source/figures/11.png){ width=50% }
