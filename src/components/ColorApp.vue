<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="container">
      <div>
        <div>Color 1</div>
        <div id="circle-1" class="circle" :style="color1"></div>
        <div id="label-1">{{ color1.text }}</div>
      </div>
      <div>
        <div>Color 2</div>
        <div id="circle-2" class="circle" :style="color2"></div>
        <div id="label-2">{{ color2.text }}</div>
      </div>
      <div>
        <div>Mixed</div>
        <div id="circle-mixed" class="circle" :style="mixed"></div>
        <div id="label-mixed">{{ mixed.text }}</div>
      </div>
      <div>
        <div>Secret</div>
        <div id="circle-secret" class="circle" :style="secret"></div>
        <div id="label-secret">{{ secret.text }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ColorApp",
  data: function () {
    return {
      color1: {
        text: "#000000",
        backgroundColor: "black",
      },
      color2: {
        text: "#000000",
        backgroundColor: "black",
      },
      mixed: {
        text: "#000000",
        backgroundColor: "black",
      },
      secret: {
        text: "#000000",
        backgroundColor: "black",
      },
    };
  },
  async mounted() {
    fetch("https://shrouded-mountain-08630.herokuapp.com/api")
      .then((res) => res.json())
      .then((data) => {
        this.color1.backgroundColor = data.color1;
        this.color2.backgroundColor = data.color2;
        this.mixed.backgroundColor = data.mixed;
        this.secret.backgroundColor = data.secret;

        this.color1.text = data.color1;
        this.color2.text = data.color2;
        this.mixed.text = data.mixed;
        this.secret.text = data.secret;

        this.$emit("loadingCheck");
      })
      .catch((err) => {
        console.log("fetch err", err);
        this.$emit("loadingCheck");
      });
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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

.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.circle {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  margin: 5px;
  background: black;
}

.container div {
  text-align: center;
  padding: 20px;
}

pre {
  background: #fafafa;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 0.5em;
  max-width: 400px;
}

ul > pre {
  max-width: 320px;
}
</style>
