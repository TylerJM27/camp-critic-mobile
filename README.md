# Welcome to your Expo app 👋

NUCAMPSITE using React Native

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

Node v. 18.20.5

NUCAMPSITE DEV NOTES: 

COMMIT - CampsiteInfoScreen:

   Folder Setup:

   - features/ inside nucampsite/
   - campsites/ inside features/

   Create CampsiteInfoScreen.js:

   - Add the file to screens/ 
   - Import RenderCampsite
   - set up function component
   - return RenderCampsite with single prop campsite={props.campsite}

   Create RenderCampsite.js:

   - Add file to campsites/
   - Import Text and View from 'react-native'
   - Import Card from 'react-native-elements'
   - Set up a function component named RenderCampsite, and destructure a property named campsite in the function's parameter list.
   - Set up an if statement to check if campsite is a truthy value. This can be done by simply passing campsite inside the parenthesis of the if statement.
   - Inside the if block, return the Card component imported from react-native-elements, passing it the prop containerStyle equal to padding: 0.
   - Between the Card component's opening and closing tags, add a Card.Image tag with a prop of source equal to campsite.image.
   - Between the Card.Image component's opening and closing tags, add a View component with a style prop, setting the following style properties:
   - Between the View component's opening and closing tags, add a Text component with a style prop, setting the following style properties:
   - Between the Text component's opening and closing tags, display the campsite name by using campsite.name inside curly brackets:
   - Below the Card.Image closing tag but still within the Card tag, add another Text component with a style prop, setting a style prop of margin: 20.
   - Between the opening and closing tags, display the campsite description within this Text component, using campsite.description inside curly braces:
   - Outside of the if statement, handle the case for when campsite is false and the code inside the if block is not returned. To do this, return an empty View component below and outside of the if statement.

   Update MainComponent.js:

   - Import the View component from 'react-native'.
   - Import the new CampsiteInfoScreen component from './CampsiteInfoScreen'.
   - In the return statement using the View component, wrap an opening and closing tag around the DirectoryScreen tag
   - Add a CampsiteInfoScreen tag below the DirectoryScreen tag, and pass the CampsiteInfoScreen a single prop named campsite equal to the following filter expression:
      - campsites.filter(campsite => campsite.id === selectedCampsiteId)[0]
   - Below the useState hook for campsites and setCampsites, create another useState hook creating a state variable named selectedCampsiteId and an update function of setSelectedCampsiteId. Leave the parentheses for useState empty, which will initialize the variable with undefined
   - Inside the DirectoryScreen opening tag, add another prop after the campsites prop called onPress. Set this equal to the callback function shown below:
   campsiteId => setSelectedCampsiteId(campsiteId)

   Update DirectoryScreen.js:

   - Add an onPress prop to the ListItem component returned from the renderDirectoryItem function used by the FlatList.
   - Set the onPress prop to an arrow function, and call the custom callback function props.onPress, passing it an argument of campsite.id.

COMMIT - Navigation and Home Screen:

   - Update App.js by: 
      - importing the NavigationContainer tag 
      - adding a opening/closing NavigationContainer tag

   - Update MainComponent.js by:
      - Remove the useState import from 'react'.
      - Remove the CAMPSITES import from '../shared/campsites'.
      - Import Platform from 'react-native'.
      - Import Constants from 'expo-constants'.
      - Import createStackNavigator from '@react-navigation/stack'.
      - Create a Function Component named DirectoryNavigator and use Stack.Navigator as a const and in a return statement
      - Remove the two const declarations making use of the useState() hook
      - Remove the DirectoryScreen and CampsiteInfoScreen tags being returned in Main
      - Add self-closing DirectoryNavigator tags inside the View Tag

   - Update DirectoryScreen.js:
      - import useState hook
      - import CAMPSITES
      - create a const variable name campsites using a useState hook with an initial value of CAMPSITES
      - set the data prop of the FlatList component to the state variable campsites
      - destructure a prop value of navigation in the parameter list of DirectoryScreen
      - change the onPress prop of the ListItem component

   -Update CampsiteInfoScreen.js:
      - destructure route prop in the parameter list of CampsiteInfoScreen function
      - destructure a campsite variable from the route.params object in the CampsiteInfoScreen function
      - pass the campsites variable in as the value of the campsites prop for the RenderCampsite component

   - Add Home Screen:
      - import Text and View from 'react-native'
      - create a Home Screen function

   - Update MainComponent.js
      - Update to include the DrawerNavigation to implement HomeScreen

   - Update Home Screen to include the featured Campsite, Promotions, and Partners data/images

COMMIT - About/Contact Screen Addition: 

   - Create an AboutScreen.js and ContactScreen.js file 

   - Using StackNavigator and Drawer.Screen, add paths to the AboutScreen and ContactScreen in the MainComponent.js file

   - Use the Card Component (and all its sub-components) to update the ContactScreen with the contact information

   - Use the Card Component (and all its sub-components) to update the AboutScreen with all of the information drawn from partners.js
      - accomplished this by using:
         - useState
         - Map method
         - ListItem with Avatar component

COMMIT - Icons, Favorites and Comments:

   - Updated CampsiteInfoScreen to display the comments for each campsite

   - Add icons to Drawer and Stack Navigators

   - Customize the side drawer in the Drawer Navigation to include a header that contains the Nucamp Image and title
      


REACT NATIVE NOTES:

WEEK 1:

Built-In React Native Components: 

   - <View> 
      - is a basic container element, very similar to the <Div> element
      - most fundamental component
   - <Text> 
      - is a basic text element
   - <FlatList>
      - renders lists from array
      - uses lazy loading - only visible items are loaded
         - similar to how when you scroll in instagram more photos load
      -In out Nucampsite:
         - Iterates through data array and send each array item to a function
         - uses KeyExtractor prop to set unique key needed by React
   - <ListItem>
      - use to display rows of information inside a container component such as View, FlatList, ScrollView
   - <Card>
      - typically used to display information about a single subject

   StyleSheet: 

   - a part of the React Native API
   - replaces CSS as there is no css as it is not a web page
   - you can put inline styles on a page:

         const styles = StyleSheet.create({
            container: {
               flex: 1,
               backgroundColor: '#fff',
               ...
            },
         });

Types of Mobile Apps:

   - Native mobile apps
      - created with specific programming language for specific OS
         - e.g. Java/Kotlin (learn Kotlin not Java) for Android & Swift/Objective C for iOS
      - Highest access to device capabilities and usually fastest
   - Mobile-first web apps:
      - Icon shortcut on phone 
      - Limited in access to full device capabilities
   - Cross-platform/ multiplatform mobile apps:
      - make it possible to use a single language and codebase to develop for multiple platforms, e.g. 
   - Hybrid apps: 
   - React Native is a cross-platform and hybrid aproach

Expo CLI: 

   - Used to scaffold out a starter site for React Native
      - like create-react-app for React
      - Third party, but reccommended officially by React Native
   - It offers other tools, mainly Expo Snack and Expo SDK

Android Emulator:

   - There is one, but it can be slower
   - It can be installed on Windows, Linux, and iOS

React Navigation - Navigators:

   - for React Native
   - It supports these common mobile application navigation patters:
      1. Drawer Navigator
      2. Stack Navigator
         - LIFO behavior - Last In, First Out, like a stack of dishes, each screen you navigate to in a stack is placed on top, then removed if you use Back functionality
         - createStackNavigator() returns two components:
            1. Navigator - used for configuring the stack navigator options
            2. Screen - used for linking a component with a screen inside the navigator
      3. Tab Navigator
      4. Switch Navigator
      5. Custom Navigator (write your own)
      - We will be using Drawer, Stack, and Tab Navigators in course

Navigation & Route Props:

   - Each component used as a screen is automatically provided with the navigator prop, which contains various functions
      - navigate() function - used in DirectoryScreen to navigate to selected campsite with onPress
      - the navigate() function takes an optional second argument of an object with parameters, can have multiple parameters
   - Each component used as a screen is also automatically provided with a route prop, which contains various information about the current route
      - route.params - used in CampsiteInfoScreen to access selected campsite ID

Drawer Navigator: 

   - We implemented a single side drawer navigator in the return statement of the Main component using the Drawer.Navigator tag
