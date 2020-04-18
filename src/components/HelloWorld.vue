<template>
  <div class="container-fluid bb-1">
    <div class="row">
      <div class="col-xl">
        <h3>Import XLSX</h3>
      </div>
    </div>
    <br>
    <div class="row">
      <div class="col-12">
        <div class="col-md-12">
          <label>Choose an Excel file: </label>&nbsp;
          <input type="file" @change="onChange" />
        </div>
      </div>
    </div>
    <xlsx-read :file="file">
      <hr />
      <!-- <xlsx-table id="table1" /> -->
      <hr />
      <xlsx-json id="json">
        <template #default="{collection}">
          <div>
            <!-- {{ collection }} -->
            {{ storedata(collection) }}
          </div>
        </template>
      </xlsx-json>
    </xlsx-read>

  </div>
</template>

<script>
/* eslint-disable */
import { XlsxRead, XlsxTable, XlsxJson } from "../../node_modules/vue-xlsx/dist/vue-xlsx.es.js"

export default {
  components: {
    XlsxRead,
    XlsxTable,
    XlsxJson
  },
  data() {
    return {
      file: null,
      jsondata: null
    };
  },
  methods: {
    onChange(event) {
      this.file = event.target.files ? event.target.files[0] : null;
    },
    storedata(collection) {
      console.log(collection)
      this.jsondata = collection
    }
  }
};
</script>
<style scoped>
label{
	font-family : BentonSans bold
}
#table1{
  align-items: center;
  color: red;
  background-color: aqua;
}
</style>
