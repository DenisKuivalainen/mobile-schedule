<template>
  <Container>
    
    <status-bar
      background-color="#3F51B5"
      bar-style="light-content"
    />

    <view v-if="firstLoad">
      <Loading />
    </view>
    <view v-else-if="operated">
      <Error />
    </view>
    <view v-else>
      <Main @getJsonData="getJsonData" v-bind:data="data" />
    </view>

  </Container>
</template>

<script>
import { Container } from 'native-base';

import Loading from './src/Loading';
import Error from './src/Error';
import Main from './src/Main';

export default {
  name: 'App',

  components: { 
    Container, 
    Loading,
    Error,
    Main
  },

  data: function() {
    return {
      firstLoad: true,
      operated: false,
      data: {},
    }
  },

  methods: {
    getJsonData() {
      fetch("http://kuivalainen.herokuapp.com/nspu/schedule?id=11393")
      .then(response => response.json())
      .then(data => {
        this.firstLoad = false;
        this.operated = data.operated;
        this.data = data.operated ? data.data : {};
      });
    },
  },

  beforeMount() {
    this.getJsonData();
  }
}
</script>

<style>

</style>
