<template>
    <root>
        <app-navigator></app-navigator>
    </root>
</template>

<script>
import React from "react";
import { Root } from "native-base";
// import { Icon } from "native-base";
import Ionicons from 'react-native-vector-icons/Ionicons';
import { createAppContainer, 
        createStackNavigator, 
        createBottomTabNavigator,
        createMaterialTopTabNavigator,
        createMaterialBottomTabNavigator } from "vue-native-router";
// tabs
import Home from "./tabs/Home";
import Settings from "./tabs/Settings";
import Contact from "./tabs/Contact";
// screens
import ShockIndex from "./screens/ShockIndex";
import Sofa from "./screens/Sofa";

const ContactStack = createStackNavigator(
    {
        Contact: {
            screen: Contact,
            navigationOptions: {
                title: 'Contact'
            },
        },
    },
    {
        initialRouteName: 'Contact',
        defaultNavigationOptions : {
            headerStyle: {
                backgroundColor: '#694fad',
                // marginTop: -28,
            },
            headerTintColor: 'white',
        },
    },
)
const SettingsStack = createStackNavigator(
    {
        Settings: {
            screen: Settings,
            navigationOptions: {
                title: 'Settings'
            },
        },
    },
    {
        initialRouteName: 'Settings',
        defaultNavigationOptions : {
            headerStyle: {
                backgroundColor: '#694fad',
            },
            headerTintColor: 'white',
        },
    },
)

const HomeStack = createStackNavigator(
    {
        Home: {
            screen: Home,
            navigationOptions: {
                title: 'Fast ER Calc',
            },
        },
        ShockIndex: {
            screen: ShockIndex,
            navigationOptions: {
                title: 'Indice de Choque'
            },
        },
        Sofa: {
            screen: Sofa,
            navigationOptions: {
                title: 'SOFA'
            },
        },
    },
    {
        initialRouteName: 'Home',
        defaultNavigationOptions : {
            headerStyle: {
                backgroundColor: '#694fad',
            },
            headerTintColor: 'white',
        },
    },
);
// const BottomTabNavigator = createBottomTabNavigator(
const MaterialTopTabNavigator = createMaterialBottomTabNavigator (
    {
        Home: {
            screen:HomeStack,
            navigationOptions: {
                title: 'Inicio',
            },
        },
        Contact: {
            screen: ContactStack,
            navigationOptions: {
                title: 'Contacto',
            } 
        },
        Settings: {
            screen: SettingsStack,
            navigationOptions: {
                title: 'Configuración',
            } 
        },
    }, 
    {
        initialRouteName: 'Home',
        defaultNavigationOptions: ({ navigation }) => ({
            barStyle: { backgroundColor: '#694fad' },
            tabBarIcon: ({ focused, horizontal, tintColor }) => {
                const { routeName } = navigation.state;
                let IconComponent = Ionicons;
                let iconName;
                if (routeName === 'Home') {
                    // iconName = `md-information-circle${focused ? '' : '-outline'}`;
                    iconName = `md-medkit`;
                } else if (routeName === 'Contact') {
                    iconName = `md-contact`;
                } else if (routeName === 'Settings') {
                    iconName = `md-settings`;
                }
                return <IconComponent name={ iconName } size={ 25 } color={ tintColor }/>
            }
        })
    }
);
const AppNavigator = createAppContainer(MaterialTopTabNavigator);

export default {
    components: { Root, AppNavigator },
}
</script>