<template>
  <app-navigator></app-navigator>
</template>

<script>

import {createAppContainer, createBottomTabNavigator, createMaterialTopTabNavigator,createStackNavigator } from "vue-native-router";

import NewsScreen from "./screens/NewsScreen.vue"
import ChatScreen from "./screens/ChatScreen.vue"
import ProfileScreen from "./screens/ProfileScreen.vue"
import RecycleScreen from "./screens/RecycleScreen.vue"
import TopScreen from "./screens/TopScreen.vue"


import * as React from 'react';

import * as Font from 'expo-font';

import Icon from 'react-native-vector-icons/FontAwesome';



const IOSTabs = createBottomTabNavigator(
  {
    News: {
      screen: NewsScreen,
      navigationOptions: ({ navigation }) => ({
          tabBarLabel: 'Новости', 
          tabBarIcon: ({ focused, tintColor }) => {
            let color = focused ? '#4286f4' : 'grey'
            return <Icon name="home" size={25}  color={color} />
          },
      }),
    },
    Chat: {
      screen:ChatScreen,
      navigationOptions: ({ navigation }) => ({
          tabBarLabel: 'Чат', 
          tabBarIcon: ({ focused, tintColor }) => {
            let color = focused ? '#4286f4' : 'grey'
            return <Icon name="comments" size={30}  color={color} />
          },
      }),
    },
    Profile:{
      screen: ProfileScreen,
      navigationOptions: ({ navigation }) => ({
          tabBarLabel: 'Профиль', 
          tabBarIcon: ({ focused, tintColor }) => {
            let color = focused ? '#4286f4' : 'grey'
            return <Icon name="user" size={25}  color={color} />
          },
      }),
    },
    Recycle: {
      screen:RecycleScreen,
      navigationOptions: ({ navigation }) => ({
          tabBarLabel: 'Переработка', 
          tabBarIcon: ({ focused, tintColor }) => {
            let color = focused ? '#4286f4' : 'grey'
            return <Icon name="recycle" size={25}  color={color} />
          },
      }),
    },
    Top: {
      screen: TopScreen,
      navigationOptions: ({ navigation }) => ({
          tabBarLabel: 'Топ', 
          tabBarIcon: ({ focused, tintColor }) => {
            let color = focused ? '#4286f4' : 'grey'
            return <Icon name="trophy" size={30}  color={color} />
          },
      }),
    }
  }
);


const StackNavigator = createStackNavigator(
  {
    IOSTabs
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components: { AppNavigator }
}
</script>
