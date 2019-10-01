<template>
  <div id="app">
    <router-view></router-view>
    <div class="">
     <!-- <div class="container py-3">
        <h3 class="m-1">Helpful links</h3>
      </div>-->
    </div>
    <br><br><br><br><br><br>
  </div>
</template>

<script>

export default {
  name: 'app',
  methods: {
    share() {
      navigator.share({
        title: 'Vue Minesweeper',
        text: 'A simple minesweeper game for 1st Athens Meetup',
        url: document.location,
      });
    },
  },
};
</script>
