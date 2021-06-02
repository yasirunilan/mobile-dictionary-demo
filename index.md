## Setting Up the Project

### Install Expo
Follow this guide on [Expo Installation](https://docs.expo.io/get-started/installation/) and set up the environment accordingly.


### Create the App
Run the following command to create the app

```shell
#Create a project name myDictionary.Select the "blank" template when prompted
expo init myDictionary

#Navigate to the project directory
cd myDictionary
```

### Running the App
```shell
expo start
```


### Modifying the App

1) Do your first change to the app by changing the displayed text.
2) Create the "components" folder.
3) Create HomeScreen.js Component.


```javascript
//App.js
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';
import HomeScreen from "./components/HomeScreen";

export default function App() {
  return (
    <View style={styles.container}>
      <HomeScreen/>
      <StatusBar style="auto" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

```javascript
//HomeScreen.js

import React from 'react';
import {View, Text} from 'react-native';


class HomeScreen extends React.Component {
    constructor(props) {
        super(props);

    }

    componentDidMount() {

    }

    render() {
        return(
            <View>
                <Text>Home Screen</Text>
            </View>
        );
    }
}

export default HomeScreen;

```

4) Update the HomeScreeen UI by adding a text field

```javascript
//HomeScreen.js

import React from 'react';
import {View, TextInput, StyleSheet, SafeAreaView} from 'react-native';


class HomeScreen extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            searchText: ''
        }

    }

    componentDidMount() {

    }

    render() {
        return(
            <SafeAreaView>
            <View>
                <View style={styles.title}>
                    <Text style={styles.titleText}>Your Mini Dictionary</Text>
                </View>
                <TextInput
                    style={styles.input}
                    onChangeText={(value)=>{
                        this.setState({searchText: value})
                    }}
                    value={this.state.searchText}
                    placeholder="Type your Text"
                />
            </View>
            </SafeAreaView>
        );
    }
}
const styles = StyleSheet.create({
    input: {
        height: 40,
        margin: 12,
        borderWidth: 1,
    },
    title: {
        alignItems: 'center'
    },
    titleText: {
        fontWeight: 'bold',
        fontSize: 30
    }
});

export default HomeScreen;

```

5) Let's add a button to search
```javascript
//HomeScreen.js

import React from 'react';
import {View, TextInput, StyleSheet, SafeAreaView, Button, Alert} from 'react-native';


class HomeScreen extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            searchText: ''
        }

    }

    componentDidMount() {

    }

    render() {
        return(
            <SafeAreaView>
            <View>
                <View style={styles.title}>
                    <Text style={styles.titleText}>Your Mini Dictionary</Text>
                </View>
                <TextInput
                    style={styles.input}
                    onChangeText={(value)=>{
                        this.setState({searchText: value})
                    }}
                    value={this.state.searchText}
                    placeholder="Type your Text"
                />

                <View style={styles.button}>
                    <Button
                        title="Search"
                        onPress={() => Alert.alert('Simple Button pressed')}
                    />
                </View>

            </View>
            </SafeAreaView>
        );
    }
}
const styles = StyleSheet.create({
    input: {
        height: 40,
        margin: 12,
        borderWidth: 1,
    },
    button: {
        height: 40,
        margin: 12,
    },
    title: {
        alignItems: 'center'
    },
    titleText: {
        fontWeight: 'bold',
        fontSize: 30
    }
});

export default HomeScreen;

```

6) Now let's show the typed text below the button

```javascript
//HomeScreen.js
import React from 'react';
import {View, TextInput, StyleSheet, SafeAreaView, Button, Alert, Text} from 'react-native';


class HomeScreen extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            searchText: ''
        }

    }

    componentDidMount() {

    }

    render() {
        return(
            <SafeAreaView>
            <View>
                <View style={styles.title}>
                    <Text style={styles.titleText}>Your Mini Dictionary</Text>
                </View>
                <TextInput
                    style={styles.input}
                    onChangeText={(value)=>{
                        this.setState({searchText: value})
                    }}
                    value={this.state.searchText}
                    placeholder="Type your Text"
                />

                <View style={styles.button}>
                    <Button
                        title="Search"
                        onPress={() => Alert.alert('Simple Button pressed')}
                    />
                </View>
                <View style={styles.searchResultText}>
                    <Text>{this.state.searchText}</Text>
                </View>

            </View>
            </SafeAreaView>
        );
    }
}
const styles = StyleSheet.create({
    input: {
        height: 40,
        margin: 12,
        borderWidth: 1,
    },
    button: {
        height: 40,
        margin: 12,
    },
    searchResultText: {
        marginHorizontal:20
    },
    title: {
        alignItems: 'center'
    },
    titleText: {
        fontWeight: 'bold',
        fontSize: 30
    }
});

export default HomeScreen;

```

7) Fetching Data and Displaying

```javascript
//HomeScreen.js
import React from 'react';
import {View, TextInput, StyleSheet, SafeAreaView, Button, Alert, Text} from 'react-native';


class HomeScreen extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            searchText: '',
            meaningText: ''
        }

    }

    searchDictionary = async () => {
        let url = 'https://api.dictionaryapi.dev/api/v2/entries/en_US/' + this.state.searchText;
        let response = await fetch(url);
        let result = await response.json();
        let meaningText = result[0].meanings[0].definitions[0].definition;
        this.setState({meaningText: meaningText})
    }

    render() {
        return(
            <SafeAreaView>
            <View>
                <View style={styles.title}>
                    <Text style={styles.titleText}>Your Mini Dictionary</Text>
                </View>
                <TextInput
                    style={styles.input}
                    onChangeText={(value)=>{
                        this.setState({searchText: value})
                    }}
                    value={this.state.searchText}
                    placeholder="Type your Text"
                />

                <View style={styles.button}>
                    <Button
                        title="Search"
                        onPress={this.searchDictionary}
                    />
                </View>
                <View style={styles.searchResultText}>
                    <Text>{this.state.meaningText}</Text>
                </View>

            </View>
            </SafeAreaView>
        );
    }
}
const styles = StyleSheet.create({
    input: {
        height: 40,
        margin: 12,
        borderWidth: 1,
    },
    button: {
        height: 40,
        margin: 12,
    },
    searchResultText: {
        marginHorizontal:20
    },
    title: {
        alignItems: 'center'
    },
    titleText: {
        fontWeight: 'bold',
        fontSize: 30
    }
});

export default HomeScreen;

```
8) Building the app
```bash
//android
expo build:android

or
expo build:android -t apk

//ios
expo build:ios
```

