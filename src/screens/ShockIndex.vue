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
                <nb-title>Indice de Choque</nb-title>
            </nb-body>
            <nb-right />
        </nb-header> -->
        <nb-content>
            <view class="result-container" :style="{ backgroundColor: shockIndexColor }">
                <nb-label>Indice: {{ shockIndex }}</nb-label>
                <nb-label>Clase: {{ shockClass }}</nb-label>
            </view>
            <nb-form>
                <nb-item floatingLabel>
                    <nb-label>Frecuencia Cardíaca</nb-label>
                    <nb-input v-bind:onChangedText="updateShockClass()" v-model="frecuenciaCardiaca" />
                </nb-item>
                <nb-item floatingLabel last>
                    <nb-label>Tensión Arterial</nb-label>
                    <nb-input v-bind:onChangedText="updateShockClass()" v-model="tensionArterial" />
                </nb-item>
            </nb-form>
        </nb-content>
  </nb-container>
</template>

<script>
export default {
    props: {
        navigation: {
            type: Object
        },
    },

    data() {
        return {
            tensionArterial: '',
            frecuenciaCardiaca: '',
            shockClass: 'none',
            shockIndexColor: 'grey'
        }
    },
    
    mounted() {
        this.title = this.navigation.getParam('title');
    },

    computed:{
        shockIndex() {
            if(this.tensionArterial){
                return this.frecuenciaCardiaca/this.tensionArterial;
            }else{
                return 'Faltan datos'
            }
        },
    },

    methods: {
        navigate(route) {
            this.navigation.navigate(route);
        },
        updateShockClass(){
            this.shockClass = this.compareShockClass()
        },
        compareShockClass(){
            if(this.shockIndex >= 0.5 && this.shockIndex <= 0.6){
                this.shockIndexColor = 'green'
                return 'normal'
            }else if(this.shockIndex > 0.6 && this.shockIndex <= 0.8){
                this.shockIndexColor = 'green'
                return '10-20 % (Shock CLASS I)'
            }else if(this.shockIndex > 0.8 && this.shockIndex <= 1){
                this.shockIndexColor = 'yellow'
                return '20-30 % (Shock CLASS II)'
            }else if(this.shockIndex > 1 && this.shockIndex <= 1.1){
                this.shockIndexColor = 'yellow'
                return '30-40 % (Shock CLASS III)'
            }else if(this.shockIndex >= 1.5 && this.shockIndex <= 2){
                this.shockIndexColor = 'red'
                return '40-50 % (Shock CLASS IV)'
            }else{
                this.shockIndexColor = 'grey'
                return 'N/A'
            }
        }
    }
}
</script>

<style>
    .header-container{
        margin-top: 24px;
    }
    .result-container{
        flex-direction: column;
        justify-content: space-between;
        align-content: center;
        padding: 15px;
    }
</style>
