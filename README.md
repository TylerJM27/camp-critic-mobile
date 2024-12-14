# Welcome to your Expo app 👋

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

Node v. 18.20.5

REACT NATIVE NOTES:

WEEK 1:

Basics: 

- <View> is a basic container element, very similar to the <Div> element
- <Text> is a basic text element

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
