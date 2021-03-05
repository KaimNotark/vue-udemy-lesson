<template>
  <div id="app">
    <!-- <img alt='Vue logo' src='./assets/logo.png' />-->

    <HelloWorld :msg="title" :alert="warning" :text="text" :person-data="person" />

    <h1 class="title" :class="[activeClass]">{{ firstName }}</h1>

    <h1 class="title" :class="{ 'active-class': isActive }">{{ num + 2 }}</h1>

    <h3 :class="classObj">{{ num > 2 ? "Number: > 2" : "Number: < 2" }}</h3>

    <a :class="[classObj, activeClass]" :[attrKey]="linkUrl">Go to Google</a>
    <br />
    <br />
    <div :style="{ 'font-size': fontSize + 'px' }" class="message" v-if="isVisibleMsg === 1">
      v-if message
    </div>
    <div class="message" v-else-if="isVisibleMsg === 2">v-else-if message</div>
    <div class="message" v-else>v-else message</div>
    <br />
    <br />
    <template v-if="isVisibleMsg === 1">
      <div class="message">v-if message</div>
    </template>
    <template v-else-if="isVisibleMsg === 2">
      <div class="message">v-else-if message</div>
    </template>
    <template v-else>
      <div class="message">v-else message</div>
    </template>
    <br />
    <br />
    <div>
      <h3>Hello {{ fullName }}</h3>
    </div>
    <div>
      <h3>Hello {{ fullNameGet }}</h3>
    </div>
    <br />
    <br />
    <input type="text" @keyup.enter="setName" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld
  },
  data: () => ({
    firstName: "Alex",
    lastName: "",
    num: 2,
    linkUrl: "https://google.com",
    attrKey: "href",
    isVisibleMsg: 1,

    activeClass: "my-class",
    isActive: true,
    fontSize: 30,

    title: "Hello!!!",
    warning: "Ahtung!!!",
    text: "Simple russian girl.",

    person: {
      name: "Denis",
      age: 30
    }
  }),

  computed: {
    fullName() {
      return `${this.firstName || "Default"} ${this.lastName || "user"}`;
    },

    fullNameGet: {
      get() {
        return `${this.firstName || "Default"} ${this.lastName || "user"}`;
      },
      // при попытке изменить значение в fullNameGet будет вызван этот сеттер
      set(value) {
        console.log(value);
        const [firstName, lastName] = value.split(" ");
        console.log(firstName, lastName);
        this.firstName = firstName;
        this.lastName = lastName;
      }
    },

    classObj() {
      return {
        "active-class": this.isActive,
        error: !this.isActive
      };
    }
  },

  methods: {
    setName(e) {
      // this.firstName = e.target.value;
      this.fullNameGet = e.target.value;
    },
    onLastNameUpdate(value) {
      console.log("watch--", value);
    }
  },

  watch: {
    lastName: "onLastNameUpdate"
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
