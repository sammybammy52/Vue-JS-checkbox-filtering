# VUE JS CODE CHALLENGE 1
# Select Type Checkbox 
# Done by Seye Samuel Yemi-Olowolabi

This project was carried out using Vue 3, bootstrap 5, and fontawesome for icons.
The project was carried out in four steps;
- Installing bootstrap
- Installing fontawesome
- Building the User Interface
- Adding functionality
## Installing Bootstrap
The bootstrap installation is pretty straightforward and only requires one line of code if you install it with the node package manager "npm". it automatically pulls in all the source files required.
```
npm install bootstrap
```
## Installing Font Awesome
- The first step in installing fontawesome is to use npm to install the core package which contains all the utilities to make the icons work
```
npm i --save @fortawesome/fontawesome-svg-core
```
- Next you will need to install the icon packages that you want to use. for the free icon packages. the various icon packages can be found on the [Font awesome](https://fontawesome.com/) website. i will be installing free solid, free regular and free brands icon packages
```
# Free icons styles
npm i --save @fortawesome/free-solid-svg-icons
npm i --save @fortawesome/free-regular-svg-icons
npm i --save @fortawesome/free-brands-svg-icons
```
- You will need to install the fontawesome vue component, this is what will be used to position the icons on the page
```
npm i --save @fortawesome/vue-fontawesome@latest-3
```
- To start adding icons, you will need to replace your src/main.js file with the following code snippet. specific icons can be imported and then added to the library for use
```
/* Set up using Vue 3 */
import { createApp } from 'vue'
import App from './App.vue'

/* import the fontawesome core */
import { library } from '@fortawesome/fontawesome-svg-core'

/* import font awesome icon component */
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

/* import specific icons */
import { faUserSecret } from '@fortawesome/free-solid-svg-icons'

/* add icons to the library */
library.add(faUserSecret)

createApp(App)
.component('font-awesome-icon', FontAwesomeIcon)
.mount('#app')
```
## Building the User Interface
The HTML markup snippet for this challenge is written below. an important aspect of this markup is that the checkboxes have been modeled to the checked array from the data method. whenever a checkbox is clicked, its value would be inside that array
```
<template>
    <div class="
        container-fluid
        d-flex
        flex-column
        aligns-items-center
        justify-content-center
        bg-dark
      ">
        <div class="row bg-dark border-bottom border-primary border-3">
            <div class="col-4 text-light pt-2 ps-4">
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" value="happy" id="flexCheckDefault"
                        v-model="checked" checked />
                    <font-awesome-icon icon="fa-solid fa-face-grin-wide" style="color: yellow; font-size: 25px" />
                </div>
            </div>
            <div class="col-4 text-light pt-2 ps-4">
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" value="meh" id="flexCheckDefault" v-model="checked"
                        checked />
                    <font-awesome-icon icon="fa-solid fa-face-meh" style="color: yellow; font-size: 25px" />
                </div>
            </div>
            <div class="col-4 text-light pt-2 ps-4">
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" value="sad" id="flexCheckDefault" v-model="checked"
                        checked />
                    <font-awesome-icon icon="fa-solid fa-face-frown" style="color: yellow; font-size: 25px" />
                </div>
            </div>
        </div>
        <div class="container-fluid" v-for="item in computedItems" :key="item.id">
            <div class="row bg-dark p-3">
                <div class="
              col-4
              text-light
              d-flex
              aligns-items-center
              justify-content-center
            ">
                    <font-awesome-icon v-bind="{ icon: item.icon }"
                        :style="{ fontSize: 25 + 'px', color: item.color }" />
                </div>
                <div class="
              col-4
              text-light
              d-flex
              aligns-items-center
              justify-content-center
            ">
                    <h5>{{item.text}}</h5>
                </div>
                <div class="
              col-4
              text-light
              d-flex
              aligns-items-center
              justify-content-center
            ">
                    <input class="
                bg-dark
                text-light
                border border-secondary border-3
                rounded
                ps-2
              " type="number" name="" id="" :value="item.id" style="width: 70%" />
                </div>
            </div>
        </div>
    </div>
</template>
```
## Adding Functionality
Next up is the script section of the project. This contains the functionality
the first thing to be done is to import the bootstrap into the prioject
```
// importing bootstrap into the project
import "bootstrap/dist/css/bootstrap.min.css";
import "bootstrap";
```
Inside our export defaults array would be using various lifecycle methods like data, mounted and we will also be using the computed method. Inside the data method we would be storing an array of the items and the categories that would be checked by default
```
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

};
```

The array of items is empty and thats because it would be coming from the mounted method.
```
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
```
Lastly we have the computed property, here lies the functionality for filtering the array of items. the method here returns an array based on the array of items and the checked array. 
If nothing is checked (checked array is empty), it returns an empty array. 
If theres something insde the checked array, it filters the array of items and only includes the ones that have their category in the checked array
```
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
```
### Thank you for reading
### - Seye Samuel Yemi-Olowolabi


