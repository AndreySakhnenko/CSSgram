<template>
  <div class="hello">
    <!-- <h1>{{ msg }}</h1> -->
    <h1 v-bind:style="{ color: myColor }" class="title">
      <svg
        v-bind:style="{ fill: myColor }"
        xmlns="http://www.w3.org/2000/svg"
        width="40"
        height="40"
        viewBox="0 0 29 29"
        class="title__logo"
      >
        <g>
          <path
            d="M8.495 3.628S4.939 4.95 2.839 9.922l11.585-2.19-5.929-4.104zm-5.831 7.003s-1.568 3.455.481 8.448l6.612-9.763-7.093 1.315zm.924 8.94s1.322 3.556 6.294 5.656L7.693 13.64l-4.105 5.931zm7.003 5.83s3.455 1.567 8.448-.481l-9.763-6.61 1.315 7.091zm9.131-.772s3.557-1.322 5.656-6.296l-11.586 2.189 5.93 4.107zm5.349-15.452l-6.61 9.763 7.093-1.316c0 .001 1.566-3.454-.483-8.447zm-.443-.492s-1.322-3.556-6.295-5.655l2.189 11.585 4.106-5.93zm-7.004-5.83s-3.453-1.568-8.447.482l9.764 6.61-1.317-7.092z"
          ></path>
          <path
            d="M14.151 0C6.336 0 0 6.336 0 14.15 0 21.963 6.335 28.3 14.151 28.3c7.813 0 14.149-6.338 14.149-14.15C28.301 6.336 21.965 0 14.151 0zm0 27.206c-7.199 0-13.057-5.857-13.057-13.056 0-7.199 5.858-13.056 13.057-13.056 7.197 0 13.055 5.857 13.055 13.056 0 7.199-5.858 13.056-13.055 13.056z"
          ></path>
        </g>
      </svg>
      CSSgram
    </h1>
    <h2 class="sub_title">
      Update CSS Variables with
      <span v-bind:style="{ color: myColor }">JS</span>
    </h2>
    <div class="top_input">
      <label for="border"> Border: </label>
      <input
        v-on:input="ranBorder"
        id="border"
        type="range"
        name="border"
        min="0"
        max="50"
        value="10"
      />
      <label for="bace-color"> Bace-color </label>
      <input
        v-on:input="ranColor"
        id="bace-color"
        type="color"
        value="#ffc600"
      />
    </div>

    <div class="content">
      <div class="content_image">
        <img v-bind:style="styleFirst" src="../assets/center.png" alt="foto" />
      </div>
      <div class="input_range">
        <div class="filter_block">
          <div class="filter">
            <label for="blur" class="label_text"> Blur: </label>
            <span class="label_span">{{ blur }}px</span>
          </div>
          <input
            v-on:input="ranBlur"
            id="blur"
            class="range"
            type="range"
            name="blur"
            min="0"
            max="20"
            value="0"
          />
        </div>
        <div class="filter_block">
          <div class="filter">
            <label for="contrast" class="label_text"> Contrast: </label>
            <span class="label_span">{{ contrast }}%</span>
          </div>
          <input
            v-on:input="ranContrast"
            id="contrast"
            class="range"
            type="range"
            name="contrast"
            min="0"
            max="200"
            value="100"
          />
        </div>
        <div class="filter_block">
          <div class="filter">
            <label for="rotate" class="label_text"> Hue Rotate: </label>
            <span class="label_span">{{ rotate }}deg</span>
          </div>
          <input
            v-on:input="ranRotate"
            id="rotate"
            class="range"
            type="range"
            name="rotate"
            min="0"
            max="360"
            value="0"
          />
        </div>
        <div class="filter_block">
          <div class="filter">
            <label for="sepia" class="label_text"> Sepia: </label>
            <span class="label_span">{{ sepia }}%</span>
          </div>
          <input
            v-on:input="ranSepia"
            id="sepia"
            class="range"
            type="range"
            name="sepia"
            min="0"
            max="100"
            value="0"
          />
        </div>
        <div class="filter_block">
          <div class="filter">
            <label for="saturate" class="label_text"> Saturate: </label>
            <span class="label_span">{{ saturate }}%</span>
          </div>
          <input
            v-on:input="ranSaturate"
            id="saturate"
            class="range"
            type="range"
            name="saturate"
            min="0"
            max="200"
            value="100"
          />
        </div>
        <button
          v-on:click="clearAll"
          v-bind:style="{ borderColor: myColor }"
          type="reset"
        >
          Clear all
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      blur: 0,
      contrast: 100,
      rotate: 0,
      sepia: 0,
      saturate: 100,
      myBorder: 10,
      myColor: 0,
    };
  },
  computed: {
    styleFirst() {
      return {
        filter: `blur(${this.blur}px) contrast(${this.contrast}%) sepia(${this.sepia}%) saturate(${this.saturate}%)`,
        transform: `rotate(${this.rotate}deg)`,
        border: `${this.myBorder}px solid #ffc600`,
        borderColor: `${this.myColor}`,
      };
    },
  },
  methods: {
    clearAll() {
      this.blur = `0`;
      this.contrast = `100`;
      this.rotate = `0`;
      this.sepia = `0`;
      this.saturate = `100`;
      this.myColor = `#ffc600`;
      this.myBorder = "10px";
    },
    ranColor(event) {
      this.myColor = event.target.value;
    },
    ranBorder(event) {
      this.myBorder = event.target.value;
    },
    ranBlur(event) {
      this.blur = event.target.value;
    },
    ranContrast(event) {
      this.contrast = event.target.value;
    },
    ranRotate(event) {
      this.rotate = event.target.value;
    },
    ranSepia(event) {
      this.sepia = event.target.value;
    },
    ranSaturate(event) {
      this.saturate = event.target.value;
    },
  },
};
</script>

<style scoped>
h1,
h2,
h3 {
  margin-top: 0;
  padding: 0;
}
svg{
  fill: #ffc600;
  height: 50px;
  width: 50px;
}
.hello {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: 30px;
}
.title {
  color: #ffc600;
  margin-bottom: 40px;
  font-size: 60px;
  font-weight: 700;
  align-items: center;
  display: flex;
  justify-content: center;
  gap: 20px;
}
.sub_title {
  font-size: 45px;
  font-weight: 700;
  margin-bottom: 35px;
  color: white;
}
.sub_title > span {
  color: #ffc600;
}
.top_input {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
  gap: 10px;
}
.content {
  padding: 5px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  gap: 20px;
}
.content_image {
  box-sizing: border-box;
  display: flex;
  padding: 10px;
}
.content_image > img {
  border: 10px solid #ffc600;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transform: rotate(0);
  filter: contrast(100%) saturate(100%);
}
.filter {
  display: flex;
  justify-content: space-between;
}
.input_range {
  display: flex;
  flex-flow: row wrap;
  align-content: space-between;
  padding: 10px;
}
label {
  font-size: 30px;
  color: white;
}
.label_text {
  padding: 5px 0;
  font-size: 20px;
}
.label_span {
  padding: 5px 0;
  font-size: 20px;
  color: white;
}
button {
  padding: 5px 10px;
  background-color: #191d23;
  color: #ffc600;
  font-size: 20px;
  border: 2px solid #ffc600;
  transition: all 1s ease-in-out;
  cursor: pointer;
}
button:hover {
  color: white;
  background-color: #ffc600;
}
.filter_block {
  width: 100%;
}
.range {
  width: 100%;
}

input[type="range"] {
  -webkit-appearance: none;
  height: 1px;
}
</style>
