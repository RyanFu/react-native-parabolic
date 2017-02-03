# react-native-parabolic

A react native component simulation of parabolic motion.

## Install

```bash
$ npm i react-native-parabolic --save
```
## Show case

### [A demo app can be found here.](https://github.com/stoneWeb/elm-react-native)

![add](https://raw.githubusercontent.com/stoneWeb/elm-react-native/master/screenshots/add.gif)

## Add it to your project

```
import Parabolic from 'react-native-parabolic'
import React, { Component } from 'react';
import {
  AppRegistry,
  StyleSheet,
  AlertIOS,
  Text,
  View
} from 'react-native';

export default class par extends Component {
  constructor(props){
    super(props)
    this.state = {}
  }
  componentDidMount(){
    setTimeout(()=>{
      this.setState({
        startX: 20,
        startY: 20,
        endX: 200,
        endY: 300
      })
      this.refs["parabolic"].run()
    }, 200)
  }
  animateEnd(){
    AlertIOS.alert("title", "动画完毕")
  }
  render() {
    return (
      <View style={styles.container}>
        <Parabolic
          ref={"parabolic"}
          style={{position: "absolute", left: 30, top: 30}}
          startX={this.state.startX}
          startY={this.state.startY}
          endX={this.state.endX}
          endY={this.state.endY}
          renderChildren={() => {
            return (
              <View style={{backgroundColor:"#f00", width: 16, height: 16, borderRadius: 8}}></View>
            )
          }}
          animateEnd={this.animateEnd.bind(this)}
          curvature={.008}
          duration={250}
        />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  }
});
```
#### Basic

| Prop           | Default  |   Type   | Description                   |
| :------------- | :------: | :------: | :---------------------------- |
| startX         |    0     | `number` | start x position.             |
| startY         |    0     | `number` | start y position.             |
| endX           |    0     | `number` | end x position.               |
| endY           |    0     | `number` | end y position.               |
| renderChildren | function |  `func`  | render children layout        |
| animateEnd     | function |  `func`  | animate end callback function |
| curvature      |  0.003   | `number` | Parabolic curvature           |
| duration       |   350    |  number  | animate duration time         |
| style          |   null   | `object` | animate element style         |
