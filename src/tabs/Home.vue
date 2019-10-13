<template>
    <nb-container>
        <!-- <nb-header class="header-container">
            <nb-left>
            <nb-button transparent
              :on-press="() => navigation.navigate('DrawerOpen')"
            >
            <nb-icon name="menu" />
                </nb-button>
            </nb-left>
            <nb-body>
                <nb-title>{{ navigation.headerTitle }}</nb-title>
            </nb-body>
            <nb-right />
        </nb-header> -->
        <nb-content>
            <nb-list>
                <nb-list-item v-for="test in tests" :key="test.id" button @press="navigate(test.route)">
                    <!-- <nb-icon style="ionicons" ios="ios-home" android="md-home" :style="{ color: '#ff0000' }"/> -->
                    <nb-text>{{ test.route }}</nb-text>
                </nb-list-item>
            </nb-list>
        </nb-content>
  </nb-container>
</template>

<script>
export default {
  // Declare `navigation` as a prop
  props: {
    navigation: {
        type: Object
    },
  },
  data() {
      return {
        tests: [
            {id: 0, name: 'Indice de Choque', route: 'ShockIndex'},
            {id: 1, name: 'SOFA', route: 'Sofa'},
        ]      
      }
  },
  methods: {
    navigate(route) {
      this.navigation.navigate(route)
    }
  }
}
</script>

<style>
    .header-container{
        margin-top: 24px;
    }
    .container{
        flex: 1;
        justify-content: center;
        align-content: center;
    }
</style>
