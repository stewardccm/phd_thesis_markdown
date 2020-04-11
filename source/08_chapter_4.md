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

### Frontend

Magento 2 is not a Model, View, Controller system. It is a system similar to Model, View, ViewModel (MVVM), but the architects have not given it a specific name.

In Magento 2, when you request a URL, the system will route the request to execute method of the Controller class, similar to the MVC system that routes the request to the action method of the Controller class. However, unlike the traditional MVC system, this Controller class is only responsible for the following things:

- Decide which page layout to use
- Handling saving data from POST requests
- One of the following two things:
  - Let the system render HTTP response
  - Redirect the user to the next or previous page

Each View is responsible for obtaining its own information from the model layer, request object, or other external systems. Magento decomposes the HTML page into many fragments, called containers. Each container contains a nested tree of objects, called blocks. Each block object has a phtml template file, which  is used to specify the HTML to be displayed by the block object. According to MVVM, the block object of Magento is the View Model. The block object will complete all data reading into CRUD models, request object, external systems, etc. The phtml template file is View in MVVM, it only interacts with ViewModel.

The traditional PHP MVC system sets the variable values in the view in the controller. Magento's approach is a bit different from the traditional one. Magento 2 uses Model, View and View Model to separate business logic and template logic. For a large development team, everyone's responsibilities are clear. This change of Magento is likely to be more beneficial to them, but it is not very good for full-stack engineers. Full-stack engineers need to consider more levels of abstraction.

Like most modern frameworks, Magento 2 uses many different cache files to speed up operations that will slow down. The purpose of these caches is to make the system run faster in production environment, but this often results in Magento not using the latest configuration or source files, so no changes can be seen. 

When create new features in the Magento 2 system, it is often necessary to clear the cache. It can use the CLI command of bin/magento, System -> Cache Management in the backend, or delete the cache file to clear Cache.

In order to speed up the system, in addition to the cache file, Magento 2 also generates many boilerplate classes. These files are placed in the var/generation path. When there has modify some configuration or code files, it is usually necessary to regenerate these files. Currently, there is no method, ever CLI or backend, that can help regenerate. The only way is to manually delete the files under var/generation.

### Database

#### ORM

Magenta is a very complete packaging framework. In addition to practicing the spirit of many design patterns, there are also some other patterns in it, such as the ORM architecture is one of them.

ORM, whose full name is Object-Relational Mapping, is a programming pattern used to convert data between different types of systems in object-oriented languages. Its role is to make an encapsulation between the associated database  and the entity, so that when we specifically operate Object, we do not need to deal with complex SQL statements, only simple operation of the object Property and Method.

During development, it often interacts with the database. Whether it is in the Controller, View or Model, it is possible to use the four major functions of the database: Insert, Delete, Select, Update and through ORM to help us package the method, we can quickly get the data we want or achieve the operation we want to do to the database.

In Magento 2 architecture, the principle of one data table is mainly corresponding to one Model. Collection is a type of operation database in Magento, which implements many database select methods, let us use a very intuitive way to obtain the data in the database, and do not need to use the long SQL syntax. Model in Magento can be said to be an entity, whether the method of insert, update and delete, can be operated through Entity. There are two ways to obtain a Collection in Magento 2 to operate the ORM. The first is to declare the Model Entity first, which is obtained by using the getCollection() method in the Entity, and the second is to directly create a Collection Class.

Using Magento to operate the database through the ORM method not only increases the readability and maintenance of the program, but also greatly improves the security of the program. It is a good way to prevent SQL injection attacks.

#### EAV

In the Magento database, there are more than three hundred data sheets, and the data structure used in it is EAV. EAV is a relationship model derived from database management technology, where E of EAV is an Entity, each entity represents an object in the Magento system, and is stored in the database with an independent ID, such as, products, orders, customers, catalog, etc. A represents the Attribute, the attribute is the nature of each object in the Magento system, for example, the product has a name, price, quantity, etc. And V is the Value, which is the value of the attributes. Magento is through such a data model to access data in various formats.

Entity is defined as entity type in Magento internal program, and the built-in Entity type has the following eight types, which can also be added manually, and the new Entity type will be added in the table of eav_entity_type.

![eav_entity_type \label{ref_a_figure}](source/figures/12.png){ width=100% }

As mentioned above, each entity has different attributes, so each Attribute will correspond to the Entity type, such as the product name, price, quantity, etc., or the customer's name, phone, address, etc., and all Attributes will be stored in eav_attribute in this table, for customers with entity_type_id of 1, the blocks in the eav_attibute table are as follows.

![eav_attibute \label{ref_a_figure}](source/figures/13.png){ width=100% }

The different values possessed by the attribute will be stored in the data table, the schematic diagram is as follows.

![catalog_category_entity_varchar \label{ref_a_figure}](source/figures/14.png){ width=100% }

Compared with other database structures, EAV has greater flexibility to allow development of expansion kits, without changing the core database structure, it is easier and faster to add attributes and data.

### API

Magenta 2 comes with APIs based on SOAP and REST. There is no longer an API based on XML-RPC. From the perspective of business logic, APIs based on SOAP and REST are equivalent. In addition to providing programmers with a way to programmatically interact with a single independent Magento instance without writing native Magento or PHP code, the Magento 2 REST API is also designed to allow browser-based client-side Javascript code to access API calls. Becasue this project uses React Native, which is mainly in Javascript, as a mobile application development, Magento 2 REST API is the main API method, so the data obtained through the API will be returned in JSON format.

Magento 2 REST APIs used in this project: 

| Name                                    | Method | Description                                                  |
| --------------------------------------- | ------ | ------------------------------------------------------------ |
| carts/mine                              | PUT    | Save quote                                                   |
| carts/mine                              | POST   | Creates an empty cart and quote for a specified customer if customer does not have a cart yet. |
| carts/mine                              | GET    | Returns information for the cart for a specified customer.   |
| carts/mine/balance/apply                | POST   | Apply store credit                                           |
| carts/mine/billing-address              | GET    | Returns the billing address for a specified quote.           |
| carts/mine/billing-address              | POST   | Assigns a specified billing address to a specified cart.     |
| carts/mine/checkGiftCard/{giftCardCode} | GET    | Check gift card balance if applied to given cart.            |
| carts/mine/collect-totals               | PUT    | Set shipping/billing methods and additional data for cart and collect totals. |
| carts/mine/coupons                      | GET    | Returns information for a coupon in a specified cart.        |
| carts/mine/coupons                      | DELETE | Deletes a coupon from a specified cart.                      |
| carts/mine/coupons/{couponCode}         | PUT    | Adds a coupon by code to a specified cart.                   |
| carts/mine/delivery-option              | POST   | Handle selected delivery option.                             |
| carts/mine/estimate-shipping-methods    | POST   | Estimate shipping by address and return list of available shipping methods. |
| carts/mine/giftCards                    | POST   | Add gift card to the cart.                                   |
| carts/mine/giftCards/{giftCardCode}     | DELETE | Remove GiftCard Account entity                               |
| carts/mine/items                        | POST   | Add/update the specified cart item.                          |
| carts/mine/items/{itemId}               | PUT    | Add/update the specified cart item.                          |
| carts/mine/items/{itemId}               | DELETE | Removes the specified item from the specified cart.          |
| carts/mine/order                        | PUT    | Places an order for a specified cart.                        |
| carts/mine/payment-information          | POST   | Set payment information and place order for a specified cart. |
| carts/mine/payment-information          | GET    | Get payment information                                      |
| carts/mine/payment-methods              | GET    | Lists available payment methods for a specified shopping cart. This call returns an array of objects, but detailed information about each object’s attributes might not be included. |
| carts/mine/totals                       | GET    | Returns quote totals data for a specified cart.              |
| carts/mine/totals-information           | POST   | Calculate quote totals based on address and shipping method. |
| products                                | GET    | Get product list                                             |
| products/cost-information               | POST   | Return product prices. In case of at least one of skus is not found exception will be thrown. |
| products/special-price-information      | POST   | Return product's special price. In case of at least one of skus is not found exception will be thrown. |
| products/{sku}                          | GET    | Get info about product by product SKU                        |
| products/{sku}/media                    | GET    | Retrieve the list of gallery entries associated with given product |
| products/{sku}/options                  | GET    | Get the list of custom options for a specific product        |
| products-render-info                    | GET    | Collect and retrieve the list of product render info. This info contains raw prices and formatted prices, product name, stock status, store_id,  etc. |
| search                                  | GET    | Make Full Text Search and return found Documents             |
| stockStatuses/{productSku}              | GET    | Get the stock statuses for a specific product                |

### React Native

#### Lifecycle

React component allows developer to divide the UI into independent and reusable units, and each unit can be drawn to  think independently. React component can be defined by inheriting React.Component or React.PureComponent. each component has several life cycle methods, developer can override these methods in order to execute certain programs at specific times during the development process. 

**Mounting**

When an instance of a component is created and added to the DOM, its lifecycle will call these methods in the following order:

- constructor()

```react
constructor(props)
```

  - A React component constructor will be called before it is mounted. Usually in React, the constructor will only serve two purposes:

    - Initialize the internal state by specifying a this.state object.
    - Bind an instance to the event handler method.

- static getDerivedStateFromProps()

```react
static getDerivedStateFromProps(props, state)
```

  - getDerivedStateFromProps will be called before a component is rendered, whether it is during the first mount or subsequent updates. It should return an object to update the state, or null to indicate that no state needs to be updated.

- render()

- componentDidMount()

  - After a component is mounted (added to the DOM tree), componentDidMount () will be called immediately. The initialization that requires DOM node should be written in this method.

**Updating**

When the prop or state changes, an update will be generated. When a component is re-rendered, its life cycle will call these methods in the following order:

- static getDerivedStateFromProps()

- shouldComponentUpdate()

- render()

- getSnapshotBeforeUpdate()

```react
getSnapshotBeforeUpdate(prevProps, prevState)
```

  - getSnapshotBeforeUpdate () will be called when the last render output is submitted to the DOM. It allows to grab some information (such as the position of the scroll axis) from the DOM before it changes. The value returned by this lifecycle method will be passed as a parameter to componentDidUpdate ().

- componentDidUpdate()

```react
componentDidUpdate(prevProps, prevState, snapshot)
```

  - componentDidUpdate () will be called immediately after the update. This method will not be called during the first render. 

  - After the component is updated, the DOM can be operated here.

  - If the component has getSnapshotBeforeUpdate () this rare life cycle method, the value returned will be passed to componentDidUpdate () as the third "snapshot" parameter. Otherwise, this parameter will be undefined.

**Unmounting**

When a component is removed from the DOM, this method will be called:

- componentWillUnmount()
  - componentWillUnmount () will be called as soon as each component is unmounted and destroyed. Developer can perform any cleanup within this method, such as canceling timers and network requests or removing any subscriptions created in componentDidMount ().

**Error handling**

When a component fails during the render process, life cycle, or in the constructor of a child component, these methods are called:

- static getDerivedStateFromError()

```react
static getDerivedStateFromError(error)
```

  - This lifecycle method will be called after an error is thrown by a descendant component. It will receive the error as its parameter and return a value to update the state.

- componentDidCatch()

```react
componentDidCatch(error, info)
```

  - This lifecycle method will be called after an error is thrown by a descendant component. It accepts two parameters:

    - error - the error being thrown.
    - info - An object with a componentStack key that contains information about which component threw an error.

  - componentDidCatch () will be called during "commit", so side effect is allowed.

### Image Classification

TensorFlow.js was released a versions for React Native and Expo applications. It allows developers to load per-trained models and train new models in the mobile application. In this project, TensorFlow.js and MobileNet per-trained model architecture will be used for to classification of input images in React Native application.

## Development Difficulties

Since the project time period limitation and the requirement of the CST student, the mainly development in this project will more force on how to use a cross-platform language can be use to built a native like mobile application that can function on both iOS and Android system. Therefore, the web store with Mangeto is only have the basic function that provided by the framework and the development of the mobile application for designers is cut off.

In addition, the version of the React Native I used is the latest version. However, some of the plugins are not yet support the latest one, like use Apple Pay / Google Pay for in-store purchase, therefore it cannot be provided in this demo. 

Lastly, the image recognition function need a huge library which have trained. During to the time limited,  MobileNet pre-trained model is used for the image recognition. The data which the model provided is not what this project need, therefore it is only for demo usage only.

## UI Design

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. [@simon_2019_tech]

### Mobile Platform

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. [@simon_2019_tech]

<<<<<<< HEAD
This is the user interface of the mobile application which call the Magento API and get the data to render.

![Index Page \label{ref_a_figure}](source/figures/01.png){ width=50% }

Index Page will show the banner, discount product, and the hot product.

![Product Detail \label{ref_a_figure}](source/figures/02.png){ width=50% }

Product Detail will show the product gallery, basic information and the option of the product. 

![Explore \label{ref_a_figure}](source/figures/03.png){ width=50% }

Search page use for search the product by keywords.

![Login \label{ref_a_figure}](source/figures/04.png){ width=50% }

#### Withoutconnect Magento API

This is the user interface of the mobile application with the dump data and for test the development function. The reason why have this version of the applicaiton is because before put one function on the connected API version, we need to see the funtion is there any error or conflict which will affect the API version.

![Index Page \label{ref_a_figure}](source/figures/05.png){ width=50% }
=======
#### Connected with Magento API

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. [@simon_2019_tech]

![(a) Index Page, (b) Product Detail](source/figures/0102.png){width=100%}

![(a) Explore, (b) Login](source/figures/0304.png){width=100%}

#### Withoutconnect Magento API

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. [@simon_2019_tech]
>>>>>>> master

![(a) Index Page, (b) Catalog](source/figures/0506.png){width=100%}

![(a) Product Detail, (b) Search](source/figures/0708.png){width=100%}

### Web Platform

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. [@blair_2019_mobile]

![Index Page \label{ref_a_figure}](source/figures/09.jpg){width=100%}

![Product Detail \label{ref_a_figure}](source/figures/10.jpg){width=100%}

![Checkout \label{ref_a_figure}](source/figures/11.png){width=100%}
