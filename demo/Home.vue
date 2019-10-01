<template>
  <div>
    <div class="container py-3">
      <h1>Vue Minesweeper</h1>
      <p class="lead">
        Ναρκαλιευτής σε VueJS 1st Athens Meetup!
      </p>
    </div>
    <div class="bg-light">
      <div class="container py-3">
        <h3>Έναρξη παιχνιδιού</h3>
        <div class="row">
          <div class="col-12 col-md-4 py-3">
            <router-link href="#" class="btn btn-lg btn-block btn-success" :to="{
              name: 'game',
              params: {
                rows: 9,
                cols: 9,
                bombs: 10,
              }}">
              <i class="fa fa-baby"></i>
              Αρχάριος (9x9)
            </router-link>
          </div>
          <div class="col-12 col-md-4 py-3">
            <router-link href="#" class="btn btn-lg btn-block btn-warning" :to="{
              name: 'game',
              params: {
                rows: 16,
                cols: 16,
                bombs: 40,
              }}">
              <i class="fa fa-user"></i>
             Προχωρημένος (16x16)
            </router-link>
          </div>
          <div class="col-12 col-md-4 py-3">
            <router-link href="#" class="btn btn-lg btn-block btn-danger" :to="{
              name: 'game',
              params: {
                rows: 16,
                cols: 30,
                bombs: 99,
              }}">
              <i class="fa fa-user-astronaut"></i>
              Αγριεμένος (16x99 με 99 βόμβες)
            </router-link>
          </div>
        </div>
      </div>
    </div>

    <form class="bg-light py-3" @submit="updateRoute">
      <div class="container">
        <h3>Φτιάξε το δικό σου ταμπλώ</h3>
        <div class="row">
          <div class="form-group col-12 col-md-4">
            <label for="input-rows">Γραμμές</label>
            <input type="number" v-model.number="rows" class="form-control"
                   min="1" max="50" id="input-rows">
          </div>
          <div class="form-group col-12 col-md-4">
            <label for="input-cols">Στήλες</label>
            <input type="number" v-model.number="cols" class="form-control"
                   min="1" max="50" id="input-cols">
          </div>
          <div class="form-group col-12 col-md-4">
            <label for="input-bombs">Βόμβες</label>
            <input type="number" v-model.number="bombs" class="form-control"
                   min="1" max="99" id="input-bombs">
          </div>
        </div>
        <div class="row">
          <div class="col-12">
            <button type="submit" class="btn btn-primary btn-sm">
              <i class="fa fa-dice"></i>
              Πάιξε τώρα
            </button>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'home',
  data() {
    return {
      rows: 9,
      cols: 9,
      bombs: 10,
    };
  },
  mounted() {
    this.initParams(this.$route.params);
  },
  methods: {
    doesItFit() {
      const { rows, cols, bombs } = this;
      if ((rows * cols) < bombs) {
        return false;
      }
      if (rows > 50) {
        return false;
      }
      if (cols > 50) {
        return false;
      }
      if (bombs > 99) {
        return false;
      }
      return true;
    },
    initParams(params) {
      const { rows, cols, bombs } = params;
      this.rows = parseInt(rows) || 9;
      this.cols = parseInt(cols) || 9;
      this.bombs = parseInt(bombs) || 10;
    },
    updateRoute(extraParams) {
      console.log('a');
      const { rows, cols, bombs } = this;
      const params = Object.assign({
        rows,
        cols,
        bombs,
      }, extraParams);

      this.$router.push({
        name: 'game',
        params,
      });
    },
  },
};
</script>
