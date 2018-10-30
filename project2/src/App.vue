<template>
  <div class='mainapp'>

    <quotabar class='component'></quotabar>
    <quotaadd class='component'></quotaadd>
    <quotalist class='component'></quotalist>

  </div>
</template>

<script>
import QuotaBar from './QuotaBar.vue'
import QuotaAdd from './QuotaAdd.vue'
import QuotaList from './QuotaList.vue'
export default{
  components:{
    'quotabar':QuotaBar,
    'quotaadd':QuotaAdd,
    'quotalist':QuotaList
  }
}

</script>

<style>
.component{
  margin:15px;
}
</style>
