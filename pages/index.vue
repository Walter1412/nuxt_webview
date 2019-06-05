<style lang="stylus">
span {
  margin: 20px;
  border: 1px solid black;
}
</style>
<template lang="pug">
.template
  span(@click="callIos") Call IOS
  span(@click="callAndroid") Call Androide

  div 成功： {{message}}
</template>

<script>
export default {
  components: {},
  props: {},
  data() {
    return {
      message: '未連通',
    }
  },
  computed: {},
  watch: {},
  created() {
    window.dialog = this.dialog
    // const dialog = this.dialog
  },
  mounted() {},
  methods: {
    dialog(sString) {
      // alert(`call javascript method is ${sString}`)
      this.message = `連通${sString}`
    },
    callIos() {
      window.webkit.messageHandlers.ToApp.postMessage('SendmessagetoSwift')
    },
    callAndroid() {
      // alert(window.native)
      window.native.hello2('abcdefg', 123)
      // document.location = 'js://webview?arg1=234&arg2=987'
      // document.location = 'js://xxx?id=asd&name=qwe'
    },
  },
}
</script>
