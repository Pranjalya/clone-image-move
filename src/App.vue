<template>
  <div id="app">
    <h1>HOWL's MOVING CASTLE</h1>
    <p>
      <button v-on:click="moveimage('up')">UP</button>
    </p>
    <p>
      <button v-on:click="moveimage('down')">DOWN</button>
    </p>
    <p>
      <button v-on:click="moveimage('left')">LEFT</button>
    </p>
    <p>
      <button v-on:click="moveimage('right')">RIGHT</button>
    </p>
    <br />
    <br />
    <img
      id="image"
      src="data:image/jpeg;base64,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"
    />
  </div>
</template>

<script>
var PouchDB = require("pouchdb").default;

export default {
  data() {
    return {
      imgLocal: {},
      imgRemote: {},
      leftpos: 0,
      toppos: 0
    };
  },
  methods: {
    syncImage: function() {
      this.imgLocal
        .put({
          _id: 1,
          leftpos: this.leftpos,
          toppos: this.toppos
        })
        .then(response => {})
        .catch(err => {
          console.log(err);
        });
    },
    loadimgpos() {
      this.imgRemote
        .allDocs({
          include_docs: true,
          attachments: true
        })
        .then(result => {
          this.leftpos = result.leftpos;
          this.toppos = result.toppos;
        })
        .catch(err => {
          console.log(err);
        });
    },
    moveimage: function(str) {
      var step = 50;
      switch (str) {
        case "down":
          var x = document.getElementById("image").offsetTop;
          x = x + step;
          document.getElementById("image").style.top = x + "px";
          break;

        case "up":
          var x = document.getElementById("image").offsetTop;
          x = x - step;
          document.getElementById("image").style.top = x + "px";
          break;

        case "left":
          var y = document.getElementById("image").offsetLeft;
          y = y - step;
          document.getElementById("image").style.left = y + "px";
          break;

        case "right":
          var y = document.getElementById("image").offsetLeft;
          y = y + step;
          document.getElementById("image").style.left = y + "px";
          break;
      }
      this.leftpos = document.getElementById("image").style.left;
      this.toppos = document.getElementById("image").style.top;
      this.syncImage();
    },
    startRep() {
      PouchDB.replicate(this.imgLocal, this.imgRemote, {
        live: true,
        retry: true
      })
        .on("change", function(info) {
          this.loadimgpos();
          document.getElementById("image").style.left = this.leftpos;
          document.getElementById("image").style.top = this.toppos;
        })
        .on("paused", function(err) {
          console.log("Replication: paused", err);
        })
        .on("active", function() {
          console.log("Replication: active");
        })
        .on("denied", function(err) {
          console.log("Replication: denied", err);
        })
        .on("complete", function(info) {
          console.log("Replication: complete", info);
        })
        .on("error", function(err) {
          console.log("Replication: change", err);
        });
    }
  },
  mounted() {
    this.imgLocal = new PouchDB("imgLocal");
    this.imgRemote = new PouchDB(
      "https://4f241480-c3c9-41c6-bb2e-98fd4cfe269e-bluemix:2d0f75eae437887122aec87b1225ad19a294f459beeb0a20fd69fb333cee4d4a@4f241480-c3c9-41c6-bb2e-98fd4cfe269e-bluemix.cloudantnosqldb.appdomain.cloud/moveapp"
    );
    this.leftpos = document.getElementById("image").style.left;
    this.toppos = document.getElementById("image").style.top;
    this.startRep();
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
#image {
  position: absolute;
  left: 500;
  top: 100;
}
</style>
