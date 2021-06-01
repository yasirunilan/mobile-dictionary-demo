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
    }
});

export default HomeScreen;

```




## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/yasirunilan/mobile-dictionary-demo/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/yasirunilan/mobile-dictionary-demo/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
