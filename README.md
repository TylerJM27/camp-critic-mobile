CAMPCRITIC MOBILE:

Node v. 18.20.5

NUCAMPSITE DEV NOTES:

COMMIT - CampsiteInfoScreen:

Folder Setup:

-   features/ inside nucampsite/
-   campsites/ inside features/

Create CampsiteInfoScreen.js:

-   Add the file to screens/
-   Import RenderCampsite
-   set up function component
-   return RenderCampsite with single prop campsite={props.campsite}

Create RenderCampsite.js:

-   Add file to campsites/
-   Import Text and View from 'react-native'
-   Import Card from 'react-native-elements'
-   Set up a function component named RenderCampsite, and destructure a property named campsite in the function's parameter list.
-   Set up an if statement to check if campsite is a truthy value. This can be done by simply passing campsite inside the parenthesis of the if statement.
-   Inside the if block, return the Card component imported from react-native-elements, passing it the prop containerStyle equal to padding: 0.
-   Between the Card component's opening and closing tags, add a Card.Image tag with a prop of source equal to campsite.image.
-   Between the Card.Image component's opening and closing tags, add a View component with a style prop, setting the following style properties:
-   Between the View component's opening and closing tags, add a Text component with a style prop, setting the following style properties:
-   Between the Text component's opening and closing tags, display the campsite name by using campsite.name inside curly brackets:
-   Below the Card.Image closing tag but still within the Card tag, add another Text component with a style prop, setting a style prop of margin: 20.
-   Between the opening and closing tags, display the campsite description within this Text component, using campsite.description inside curly braces:
-   Outside of the if statement, handle the case for when campsite is false and the code inside the if block is not returned. To do this, return an empty View component below and outside of the if statement.

Update MainComponent.js:

-   Import the View component from 'react-native'.
-   Import the new CampsiteInfoScreen component from './CampsiteInfoScreen'.
-   In the return statement using the View component, wrap an opening and closing tag around the DirectoryScreen tag
-   Add a CampsiteInfoScreen tag below the DirectoryScreen tag, and pass the CampsiteInfoScreen a single prop named campsite equal to the following filter expression:
    -   campsites.filter(campsite => campsite.id === selectedCampsiteId)[0]
-   Below the useState hook for campsites and setCampsites, create another useState hook creating a state variable named selectedCampsiteId and an update function of setSelectedCampsiteId. Leave the parentheses for useState empty, which will initialize the variable with undefined
-   Inside the DirectoryScreen opening tag, add another prop after the campsites prop called onPress. Set this equal to the callback function shown below:
    campsiteId => setSelectedCampsiteId(campsiteId)

Update DirectoryScreen.js:

-   Add an onPress prop to the ListItem component returned from the renderDirectoryItem function used by the FlatList.
-   Set the onPress prop to an arrow function, and call the custom callback function props.onPress, passing it an argument of campsite.id.

COMMIT - Navigation and Home Screen:

-   Update App.js by:

    -   importing the NavigationContainer tag
    -   adding a opening/closing NavigationContainer tag

-   Update MainComponent.js by:

    -   Remove the useState import from 'react'.
    -   Remove the CAMPSITES import from '../shared/campsites'.
    -   Import Platform from 'react-native'.
    -   Import Constants from 'expo-constants'.
    -   Import createStackNavigator from '@react-navigation/stack'.
    -   Create a Function Component named DirectoryNavigator and use Stack.Navigator as a const and in a return statement
    -   Remove the two const declarations making use of the useState() hook
    -   Remove the DirectoryScreen and CampsiteInfoScreen tags being returned in Main
    -   Add self-closing DirectoryNavigator tags inside the View Tag

-   Update DirectoryScreen.js:
    -   import useState hook
    -   import CAMPSITES
    -   create a const variable name campsites using a useState hook with an initial value of CAMPSITES
    -   set the data prop of the FlatList component to the state variable campsites
    -   destructure a prop value of navigation in the parameter list of DirectoryScreen
    -   change the onPress prop of the ListItem component

-Update CampsiteInfoScreen.js: - destructure route prop in the parameter list of CampsiteInfoScreen function - destructure a campsite variable from the route.params object in the CampsiteInfoScreen function - pass the campsites variable in as the value of the campsites prop for the RenderCampsite component

-   Add Home Screen:

    -   import Text and View from 'react-native'
    -   create a Home Screen function

-   Update MainComponent.js

    -   Update to include the DrawerNavigation to implement HomeScreen

-   Update Home Screen to include the featured Campsite, Promotions, and Partners data/images

COMMIT - About/Contact Screen Addition:

-   Create an AboutScreen.js and ContactScreen.js file

-   Using StackNavigator and Drawer.Screen, add paths to the AboutScreen and ContactScreen in the MainComponent.js file

-   Use the Card Component (and all its sub-components) to update the ContactScreen with the contact information

-   Use the Card Component (and all its sub-components) to update the AboutScreen with all of the information drawn from partners.js
    -   accomplished this by using:
        -   useState
        -   Map method
        -   ListItem with Avatar component

COMMIT - Icons, Favorites and Comments:

-   Updated CampsiteInfoScreen to display the comments for each campsite

-   Add icons to Drawer and Stack Navigators

-   Customize the side drawer in the Drawer Navigation to include a header that contains the Nucamp Image and title

COMMIT - Redux for React Native:

-   Set up json-server to server our data

-   Configure the creation of the Redux store

-   Set up slice reducers in separate files to be used in creating the Redux store

-   Set up React Native app to connect the components to Redux

-   Obtain state information from Redux

-   Dispatch actions to the Redux store to update the state

-   Create a new loading component, using the ActivityIndicator component from React Native

-   Update the other components fo that they show the Loading component while data is being fetched from the server, or an error if an error returned from the fetch call to the server

-   Set up a new array property in Redux store to track favorites

-   Set up a case reducer to handle adding and removing favorites in the store

-   Update the CampsiteInforScreen component to use Redux to handle tracking favorites

COMMIT - Forms and Modals:

-   Used Switch, Picker, and DateTimePicker to create a form

-   Use the local component state to store the form data, and write an event handler to handle the form submissions

-   Add the new component into the drawer and stack navigatin for your application

-   Added a Modal component that can be opened from the Reservation screen
    -   Set a local state variable to show and hide the modal

COMMIT - Favorites, Swipe Option Buttons, and Alerts:

-   Create a new componment called FavoritesScreen

    -   it will show a list of the campsites that have been marked as a favorite.

-   Update the navigation for the mobile application so that the FavoritesScreen can be accessed as a Stack Navigator from the Drawer Navigator

    -   enable navigating from the FavoritesScreen to the CampsiteInfoScreen by clicking on a campsite in the list of favorites

-   Learn to use a swipe gesture to reveal option buttons

-   Enable tapping on a delete option button to remove a favorite

-   Learn to use React Native's built-in Alert API to show an alert dialog with configurable buttons

-   Take an action upon user confirmation

COMMIT - Animations & Animatable:

-   Add an animation to the Home screen, using React Native's Animated API

-   Learn to use react-native-animatable
    -   a library built on top of the React Native Animated library
    -   gives you pre-packaged animations that can be easily applied to components

COMMIT - Gestures:

-   Learn to use the React Native built-in API called PanResponder to support gestures in your app

-   Learn to use animations to give visual feedback to users in response to a gesture

COMMIT - Persist Redux Store:

-   Set up and configure redux-persist

-   Learn to persist the Redux store and rehydrate it when the application is reloaded

COMMIT - Week 3 Workshop Assignment:

-   Add animations to the form in the Reservation screen
    -   When the user submits the form, you will pop up a confirmation alert
    -   Also, added new gesture support to the RenderCampsite component

COMMIT - Secure Store API:

-   Learned and implemented the Expo SecureStore API to store small amounts of encrypted data in key-value pairs on user's device

    -   including how to set, get and delete the data using a unique key
    -   used each method - getItemAsync, setItemAsync, and deleteItemAsync

-   Create a new login screen that contains a form, and uses the SecureStore API to store the login credentials

COMMIT - Expo Notifications API:

-   Learned and implemented methods to handle both local (client-side) and push (remote, server-generated) notifications on device

-   Use the Expo Notifications API to generate local notifications, as well as get permissions from the device to send the local notifications

COMMIT - Social Sharing:

-   Learned and implemented two social sharing APIs; MailComposer from Expo SDK and Share from React Native

-   Configured the Expo MailComposer API along with a RNE Button component to open the default email client on the device to a new email with the recipient email, subject and body fields filled in.

-   Set up React Native Share API to share information to social media accounts

COMMIT - Picking/Editing an Image:

-   Used the Expo ImagePicker API, which allows the user to choose an image for use in the application by either taking a new photo or by choosing an existing image

-   Also used the Expo ImageManipulator API, which allows user to make edits to an existing image

-   Implemented tabbed navigation with React Navigation

-   Update a parent stack navigator's options based on the nested navigator's state

-   Added a form to the Register tab in the Login Screen

-   Learn to use the ImagePicker API from Expo to obtain an image for use in the app by taking a photo with the mobile device's camera

COMMIT - Network Info:

-   Utilized the react-native-community NetInfo library to access network state information for user's device

-   Used the NetInfo library to obtain network information

-   Respond to changes in the network info by displaying a message using React Native's ToastAndroid API for Android, or its Alert API for iOS

COMMIT - Week 4 Workshop Assignment:

-   Used Expo APIs to manipulate images and access saved images, as well as convert from then-based promise handling to using async/await

-   Used Expo Media Library to save images taken in app to devices camera roll
