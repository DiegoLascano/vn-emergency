<template>
    <nb-container>
        <!-- <nb-header class="header-container">
            <nb-left>
                <nb-button transparent
                    @press="navigation.goBack()"
                >
                <nb-icon name="arrow-back" />
                    </nb-button>
            </nb-left>
            <nb-body>
                <nb-title>SOFA</nb-title>
            </nb-body>
            <nb-right />
        </nb-header> -->
    </nb-container>
</template>

<script>
import React from 'react';
import {Text} from 'react-native';
export default {
    props: {
        navigation: {
            type: Object
        }
    },
    data() {
        return {
            tests: [
                {key: '0', name: 'Indice de Choque', route: 'ShockIndex'},
                {key: '1', name: 'SOFA', route: 'Sofa'},
            ]   
        }
    },
    methods: {
        renderList: function(item) {
            return (<Text>{item.item.name}</Text>)
        },
        goBack(){
            this.navigation.goBack()
        }
    },
}
</script>

<style>
    .header-container{
        margin-top: 24px;
    }
    .shock-container{
        flex: 1;
        justify-content: center;
        align-content: center;
    }
</style>
