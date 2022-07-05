<template>
  <div
    class="
      container-fluid
      d-flex
      flex-column
      aligns-items-center
      justify-content-center
      bg-dark
    "
  >
    <div class="row bg-dark border-bottom border-primary border-3">
      <div class="col-4 text-light pt-2 ps-4">
        <div class="form-check">
          <input
            class="form-check-input"
            type="checkbox"
            value="happy"
            id="flexCheckDefault"
            v-model="checked"
            checked
          />
          <font-awesome-icon
            icon="fa-solid fa-face-grin-wide"
            style="color: yellow; font-size: 25px"
          />
        </div>
      </div>
      <div class="col-4 text-light pt-2 ps-4">
        <div class="form-check">
          <input
            class="form-check-input"
            type="checkbox"
            value="meh"
            id="flexCheckDefault"
            v-model="checked"
            checked
          />
          <font-awesome-icon
            icon="fa-solid fa-face-meh"
            style="color: yellow; font-size: 25px"
          />
        </div>
      </div>
      <div class="col-4 text-light pt-2 ps-4">
        <div class="form-check">
          <input
            class="form-check-input"
            type="checkbox"
            value="sad"
            id="flexCheckDefault"
            v-model="checked"
            checked
            
          />
          <font-awesome-icon
            icon="fa-solid fa-face-frown"
            style="color: yellow; font-size: 25px"
          />
        </div>
      </div>
    </div>
    <div class="container-fluid" v-for="item in computedItems" :key="item.id">
      <div class="row bg-dark p-3">
        <div
          class="
            col-4
            text-light
            d-flex
            aligns-items-center
            justify-content-center
          "
        >
          <font-awesome-icon
            v-bind="{ icon: item.icon }"
            :style="{ fontSize: 25 + 'px', color: item.color }"
          />
        </div>
        <div
          class="
            col-4
            text-light
            d-flex
            aligns-items-center
            justify-content-center
          "
        >
          <h5>{{item.text}}</h5>
        </div>
        <div
          class="
            col-4
            text-light
            d-flex
            aligns-items-center
            justify-content-center
          "
        >
          <input
            class="
              bg-dark
              text-light
              border border-secondary border-3
              rounded
              ps-2
            "
            type="number"
            name=""
            id=""
            :value="item.id"
            style="width: 70%"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// importing bootstrap into the project
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap";

export default {
  name: "App",
  components: {},

  data() {
    return {
      checked: [
        "happy",
        "sad",
      ],
      items: [],
    };
  },

  mounted() {
    this.items = [
      {
        id: 1,
        text: "food",
        category: "happy",
        icon: "fa-solid fa-burger",
        color: "yellow"
      },

      {
        id: 2,
        text: "games",
        category: "happy",
        icon: "fa-solid fa-chess",
        color: "purple"

      },

      {
        id: 3,
        text: "bills",
        category: "sad",
        icon: "fa-solid fa-money-bill-1-wave",
        color: "green"
      },

      {
        id: 4,
        text: "illness",
        category: "sad",
        icon: "fa-solid fa-bed-pulse",
        color: "red"
      },
    ];
  },
  computed: {
    computedItems(){
      if (this.checked.length === 0) {
        return [];
      } else {
        return this.items.filter(item =>
          this.checked.indexOf(item.category) !== -1 
        );  
      }
    }
  }
};
</script>

<style>
</style>
