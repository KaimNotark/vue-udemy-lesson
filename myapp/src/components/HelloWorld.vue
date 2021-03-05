<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <h2>{{ alert }}</h2>

    <p>{{ text }}</p>

    <p>{{ personData }}</p>

    <br />
    <br />

    <input type="text" v-model="textInput" />
    <input type="text" v-model="textComp" />
    <h3>
      Input text value:
      <i>{{ textInput }}</i>
    </h3>

    <br />
    <br />

    <input type="checkbox" v-model="checkbox" />
    <h3>
      Checkbox value:
      <i :style="{ color: color }">{{ checkbox }}</i>
    </h3>

    <input type="checkbox" v-model="checkboxArray" value="one" />
    <input type="checkbox" v-model="checkboxArray" value="two" />
    <input type="checkbox" v-model="checkboxArray" value="three" />
    <h3>
      Checkbox value:
      <i>{{ checkboxArray }}</i>
    </h3>

    <select v-model="select">
      <option value="bmv">BMW</option>
      <option value="audi">Audi</option>
      <option value="mers">Mersedes</option>
    </select>
    <h3>
      Select value:
      <i>{{ select }}</i>
    </h3>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({
    textInput: "",
    checkbox: false,
    color: "red",
    checkboxArray: [],
    select: ""
  }),

  watch: {
    checkbox: "changeCheckbox"
  },

  methods: {
    changeCheckbox(val) {
      console.log(val);
      val ? (this.color = "red") : (this.color = "green");
    }
  },

  computed: {
    textComp: {
      get() {
        return this.textInput;
      },
      set(val) {
        console.log(val);
        this.textInput = val;
      }
    }
  },

  props: {
    msg: String,
    alert: [String, Number],
    text: {
      type: String,
      default: "I'm",
      required: false
    },

    user: {
      type: Object,
      default: () => ({})
    },

    personData: {
      type: Object,
      // валидатор обязательно должен возвращать true or false
      validator(value) {
        console.log(value);
        return value.name;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
