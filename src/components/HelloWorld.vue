<template>
<div class="body">
  <div class="hello">
    <div class="b"></div>
    <div class="header">
      <h4 contenteditable>{{ msg }}</h4>
      <h4 contenteditable>[NAWP]</h4>
      <p contenteditable>Bad thing they sweet</p>
    </div>
    <div>
      <div class="imgDiv">
        <div v-if="!ImagePre">
          <img
            src="../assets/img.webp"
            alt="Vue logo"
            @click="Upload"
            ref="fileInput"
          />
        </div>
        <img
          v-else
          v-bind:src="ImagePre"
          alt="Vue logo"
          @click="Upload"
          ref="fileInput"
        />
        <input
          type="file"
          style="display: none"
          v-on:change="previewUpload"
          id="inputFile"
        />
      </div>

      <div>
        <div class="row">
          <p class="title" style="font-size: xxsmall">
            ID Number: <span contenteditable> {{ randomNumber }} </span>
          </p>
        </div>
        <div class="row">
          <p class="title">Name:</p>
          <p contenteditable>Peter Innocent</p>
        </div>
        <div class="row">
          <p class="title">Position:</p>
          <p contenteditable>PRO</p>
        </div>
        <div class="row">
          <p class="title">Zone:</p>
          <p contenteditable>Benin Zone 1</p>
        </div>
        <div class="row">
          <p class="title">State:</p>
          <p contenteditable>Edo State</p>
        </div>
      </div>
      <p style="margin: auto; width: 100%">https://nawp.netlify.app</p>
    </div>
  </div>
</div>
  <a id="download" download="NAWP">
    <button @click="Download">Download</button>
  </a>
  <footer>
    <p>Power by Innocent Peter Technology</p>
    <div class="foot-row">
      <a href="https://www.facebook.com/profile.php?id=100004849866620">
        Facebook</a
      >

      <a href="https://twitter.com/innocenpeter?t=I1lem_8XVkvtBvMuVKNyrQ&s=09"
        >Twitter</a
      >
    </div>
  </footer>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      ImagePre: false,
      randomNumber: Math.floor(Math.random() * 1996) + 2003,
    };
  },

  methods: {
    previewUpload(e) {
      var reader,
        files = e.target.files;

      reader = new FileReader();
      reader.onload = (e) => {
        this.ImagePre = e.target.result;
      };
      reader.readAsDataURL(files[0]);
    },
    Download() {
      html2canvas(document.querySelector(".body")).then((canvas) => {
        var ims = canvas.toDataURL("image/jpeg", 1.0);
        var mom = document.querySelector("#download");
        mom.download = "NAWP.png";
        mom.href = ims;

        // downloadLink.href = linkSource;
        // downloadLink.download = fileName;
        // downloadLink.click();

        mom.click();
        // document.querySelector('.hello').appendChild(canvas);
      });
    },
    Upload() {
      var input = document.querySelector("#inputFile").click();
      // console.log(input.value);

      // var imge = document.querySelector("img");
      // imge.src = URL.createObjectURL(input.target.files[0]);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.body{
margin: 3rem;
padding: 3rem;
}
div.hello::after {
  content: "";
  top: 10rem;
  z-index: -20;
  margin: 5rem;
  padding: 3rem;
  display: flex;
  border-radius: 50%;
  position: absolute;
  align-items: center;
  justify-content: center;
  background: rgba(189, 79, 79, 0.53);
}
div.hello {
  z-index: 9;
  margin: auto;
  width: 16rem;
  padding: 0.3rem;
  max-height: 1fr;
  overflow: hidden;
  position: relative;
  border-radius: 1rem;
  border: 1px solid gray;
  background-color: white;
  /* box-shadow: 0.3rem 0.3rem 0.6rem rgb(104, 107, 111); */
}

.b {
  top: -10;
  margin: 0;
  right: 0;
  height: 1rem;
  width: 40rem;
  z-index: -19;
  position: absolute;
  transform: rotate(-10deg);
  background: rgb(238, 62, 62);
  border: 1rem solid rgb(238, 62, 62);
}
.header {
  z-index: 100 !important;
}
.header h4 {
  z-index: 10;
  margin: 0.3rem;
  padding: 0.3rem;
  margin-top: 0.6rem;
  text-transform: uppercase;
}
p {
  margin: 0;
  padding: 0;
  font-size: smaller;
}
span {
  font-weight: bold;
}
.imgDiv {
  width: 6rem;
  display: flex;
  padding: 0.1rem;
  overflow: hidden;
  border-radius: 50%;
  margin: 0.6rem auto;
  align-content: center;
  justify-content: center;
  border: 1px solid #000;
}
img {
  width: 7rem;
  height: 9rem;
  cursor: pointer;
  object-fit: contains;
}
.row {
  display: flex;
  margin: 0.5rem;
  padding: 0.3rem;
  flex-direction: row;
}
.row p:nth-child(2) {
  width: 100%;
  cursor: pointer;
  padding: 0.1rem;
  text-align: justify;
  text-transform: capitalize;
  border-bottom: 2px dashed rebeccapurple;
}
.title {
  margin-right: 0.3rem;
}
button {
  width: 15rem;
  margin: 0.4rem;
  cursor: pointer;
  padding: 0.5rem;
  transition: 3s;
  border-radius: 2rem;
  border: 0.2rem solid rgb(117, 117, 214);
  box-shadow: inset 0.3rem 0.3rem 0.3rem rgb(174, 175, 177);
}
button:hover {
  box-shadow: 0.3rem 0.3rem 0.6rem rgb(175, 177, 179);
}
footer {
  width: 100%;
  margin: auto;
  display: flex;
  align-items: center;
  margin-bottom: 0.2rem;
  flex-direction: column;
  vertical-align: middle;
  justify-content: center;
}
footer p {
  width: 100%;
  display: flex;
  margin: 0.21rem;
  font-size: large;
  font-size: medium;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  border: none !important;
}
footer div {
  display: flex;
  align-items: center;
  justify-content: center;
}
footer div a {
  color: inherit;
  padding: 1rem;
  margin: 0.3rem;
  transition: 2s;
  text-decoration: none;
}
footer div a:hover {
  font-size: x-small;
  cursor: pointer;
  transform: scale(2);
  color: rgb(62, 38, 197);
}
</style>
