<template>
  <div class="row row-cols-1 row-cols-md-2">
    <div class="col mb-4">
      <div class="card h-100">
        <img
          src="https://gamepedia.cursecdn.com/dragalialost_gamepedia_en/9/93/TW02_100401_IMG_01_01.png?version=27611110df639f98154b22ce654d6aff"
          class="card-img-top"
          alt
        />
        <div class="row row-cols-1 row-cols-md-2">
          <div class="card-body col md-4">
            <div class="btn-group-vertical">
              <button type="button" @click="increaseLevel" class="btn btn-outline-secondary up shadow-none">
                <svg
                  class="bi bi-caret-up-fill"
                  width="1em"
                  height="1em"
                  viewBox="0 2 16 16"
                  fill="currentColor"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M7.247 4.86l-4.796 5.481c-.566.647-.106 1.659.753 1.659h9.592a1 1 0 0 0 .753-1.659l-4.796-5.48a1 1 0 0 0-1.506 0z"
                  />
                </svg>
              </button>
              <div class="input-group">
                <input type="text" v-model="currentLevel"/>
              </div>
              <button type="button" @click="decreaseLevel" class="btn btn-outline-secondary down shadow-none ">
                <svg
                  class="bi bi-caret-down-fill"
                  width="1em"
                  height="1em"
                  viewBox="0 0 16 16"
                  fill="currentColor"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M7.247 11.14L2.451 5.658C1.885 5.013 2.345 4 3.204 4h9.592a1 1 0 0 1 .753 1.659l-4.796 5.48a1 1 0 0 1-1.506 0z"
                  />
                </svg>
              </button>
            </div>
          </div>
          <div class="card-body col md-4">
              <p>{{totalRupies}} Rupies</p>
              <p>{{totalBronzeOrbs}} Flame Orb</p>
              <p>{{totalSilverOrbs}} Blaze Orb</p>
              <p>{{totalGoldOrbs}} Inferno Orb</p>
              <p>{{totalPlatinumOrbs}} Incandescence Orb</p>
              <p>{{totalRainbowOrbs}} Rainbow Orb</p>
          </div>
        </div>
      </div>
    </div>
    <div class="col mb-4">
      <div class="card h-100">
        <img src class="card-img-top" alt />
        <div class="card-body">
          <h5 class="card-title">Card title</h5>
          <p class="card-text">This is a short card.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
const API_URL = "http://localhost:7000/altars";
export default {
  name: "FireAltar",
  data: () => ({
    max: 2,
    element: "Flame",
    currentLevel: 0,
    altars: [],
    totalRupies: 0,
    totalBronzeOrbs: 0,
    totalSilverOrbs: 0,
    totalGoldOrbs: 0,
    totalPlatinumOrbs: 0,
    totalRainbowOrbs: 0,

  }),
  mounted() {
    fetch(API_URL)
      .then(response => response.json())
      .then(result => {
        console.log(result);
        this.altars = result;
      });
  },
  methods: {
    increaseLevel: function() {
        if (this.currentLevel == 40) return;
        if (this.currentLevel >= 0 && this.currentLevel <= 39) this.currentLevel++;
    },
    decreaseLevel: function() {
        if (this.currentLevel == 0) return;
        if (this.currentLevel >= 1 && this.currentLevel <= 40) this.currentLevel--;
    }
  },
  computed: {
      totalMaterialsAndRupiesButton: function() {

      },
      totalMaterialsAndRupiesInput: function() {

      }
  }
};
</script>

<style scoped>
img {
  max-width: 10em;
  max-height: 10em;
  margin: auto;
}

input {
  max-width: 3em;
  text-align: center;
  margin-top: -1px;
}

.up {
  margin-top: 1px;
}

p {
    margin-bottom: 0px;
}

.btn-group-vertical {
    margin-top: 1em;
    margin-left: 3em;
}
</style>
