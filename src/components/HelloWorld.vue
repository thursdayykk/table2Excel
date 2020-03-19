<template>
  <div class="hello">
    <table2Excel />
  </div>
</template>

<script>
import table2Excel from "./cmp/Table2Excel"
export default {
  name: 'HelloWorld',
  components:{table2Excel},
  data () {
    return {

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
