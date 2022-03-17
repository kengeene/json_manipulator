<!-- eslint-disable max-len -->
<template>
<div>
  <div class="hello">
    <h1>Output options</h1>
    <div class="text__options">
      <div  class="text__option">
    <input type="checkbox" id="toLowerCase" value="toLowerCase" v-model="toLowerCase">
    <label for="toLowerCase">Convert keynames to lowercase</label>
      </div>

      <div  class="text__option">
    <input type="checkbox" id="replaceWhiteSpace" value="replaceWhiteSpace" v-model="replaceWhiteSpace">
    <label for="toLowerCase">Replace whitespace with underscores</label>
      </div>
    </div>
    <h1>Input text here:</h1>
    <textarea v-model="inputText" class="text-box"/>
    <h1>Output text:</h1>
    <textarea v-model="outputText" class="text-box"/>
  </div>
</div>
</template>

<script>
export default {
  name: 'Converter',
  watch: {
    inputText() {
      this.delayedConversion();
    },
    toLowerCase() {
      this.delayedConversion();
    },
    replaceWhiteSpace() {
      this.delayedConversion();
    },
  },
  data() {
    return {
      inputText: null,
      outputText: null,
      width: 500,
      height: 500,
      toLowerCase: true,
      replaceWhiteSpace: true,
    };
  },
  methods: {
    convertText() {
      this.outputText = null;
      // eslint-disable-next-line no-console
      const parsedJSON = { ...JSON.parse(this.inputText) };
      const newObject = {};

      Object.keys(parsedJSON).forEach((key) => {
        let keyName = key;
        if (this.toLowerCase === true) {
          keyName = `${key.toLowerCase()}`;
        }
        if (this.replaceWhiteSpace === true) {
          keyName = `${key.replaceAll(' ', '_')}`;
        }
        newObject[`${keyName.toLowerCase().replaceAll(' ', '_')}`] = parsedJSON[`${key}`];
      });

      this.outputText = JSON.stringify(newObject, null, 2);
    },
    delayedConversion() {
      // setTimeout(2000);
      this.convertText();
    },
  },
};
</script>

<style lang="scss" scoped>
$text-box-width: 60%;
$text-box-height: 500px;

.text-box{
  height: $text-box-height;
  width: $text-box-width;
}
.text{
  &__options{
    display: inline-flex;
  }
  &__option{
    margin: 10px;
  }
}
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
