<template>
  <div id="appWrapper">
    <landing-view />
  </div>
</template>
<script>
import landingView from './components/landingView';

export default {
  name: 'app',
  components: {
    landingView,
  }
}
</script>
<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Montserrat:500,700,800');
  body {
    font-family: 'Montserrat', sans-serif;
    margin: 0 !important;
    color: #111111;
    background-color: #efefef;
  }
  /* width */
  ::-webkit-scrollbar {
    width: 14px;
  }
  /* Track */
  ::-webkit-scrollbar-track {
    background: #eeeeee;
  }
  /* Handle */
  ::-webkit-scrollbar-thumb {
    background: #aaaaaa;
    border: 2.5px solid #eeeeee;
    border-radius: 7px;
  }
  /* Handle on hover */
  ::-webkit-scrollbar-thumb:hover {
    background: #9f9f9f;
  }
</style>
