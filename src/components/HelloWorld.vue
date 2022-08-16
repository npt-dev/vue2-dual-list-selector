<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="columns">
      <div class="column"><b-table :data="dataList" :columns="columns"></b-table></div>
      <div class="column"><b-table :data="dataList" :columns="columns"></b-table></div>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      columns: [
        {
          field: "first_name",
          label: "First Name",
          centered: true,
        },
      ],
    };
  },
  computed: {
    dataList() {
      const result = [];
      for (let i = 0; i < 10; i++) {
        result.push({
          id: i,
          first_name: `$${i}_Default_Name_${i}`,
        });
      }
      return result;
    },
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
</style>
