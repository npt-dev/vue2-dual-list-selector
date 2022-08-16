<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <section class="section is-medium">
      <div class="columns">
        <div class="column">
          <section>
            <b-field>
              <b-table
                :data="dataList"
                :columns="columns"
                :selected.sync="selected"
                focusable
              >
              </b-table>
            </b-field>
          </section>
        </div>
        <div class="column is-one-fifth"></div>
        <div class="column">
          <b-table
            :data="dataSelected"
            :columns="columns"
            :selected.sync="deSelected"
            focusable
          >
          </b-table>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    const data = [];
    for (let i = 0; i < 10; i++) {
      data.push({
        id: i,
        first_name: `$${i}_Default_Name_${i}`,
      });
    }
    return {
      dataList: data,
      selected: {},
      deSelected: {},
      dataSelected: [],
      columns: [
        {
          field: "first_name",
          label: "First Name",
          centered: true,
        },
      ],
    };
  },
  watch: {
    selected(newItem, oldItem) {
      console.log("OLD: ", oldItem);
      const index = this.dataList.findIndex((el) => el.id === newItem.id);
      if (index < 0) return;
      this.dataSelected.push(this.dataList[index]);
      this.dataList.splice(index, 1);
      this.dataSelected.sort((a, b) => a.id.toString().localeCompare(b.id.toString()));
    },
    deSelected(newItem, oldItem) {
      console.log("OLD: ", oldItem);
      const index = this.dataSelected.findIndex((el) => el.id === newItem.id);
      if (index < 0) return;
      this.dataList.push(this.dataSelected[index]);
      this.dataSelected.splice(index, 1);
      this.dataList.sort((a, b) => a.id.toString().localeCompare(b.id.toString()))
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
