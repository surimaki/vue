<template>
  <div id="app">
    <div>
      Name : <input v-model="form.name">
    </div>
    <div style="padding-top: 40px;">
      Age : <input v-model="form.age">
    </div>
    <div style="padding-top: 20px;">
      <button
        v-if="isEdit"
        @click="update()">
        update
      </button>
      <button
        v-else
        @click="add()">
        submit
      </button>
    </div>
    <div style="padding-top: 40px;">
      <table class="table" border="1">
        <tr>
          <th> Name </th>
          <th> Age </th>
          <th> Edit</th>
          <th> Delete</th>
        </tr>
        <tr v-for="(item, i) in items" :key="i">
          <td>
            {{ item.name}}
          </td>
          <td>
            {{ item.age}}
          </td>
          <td>
            <button @click="setUpdate(item, i)">
              Edit  
            </button>
          </td>
          <td>
            <button @click="remove(i)">
              Delete 
            </button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'APP',
  data () {
    return {
      form: {
        name: '',
        age: 0
      },
      items: [
        {
          name : 'Mark',
          age : 18
        },
        {
          name : 'kellen',
          age : 19
        },
        {
          name : 'Win',
          age : 20
        },
      ],
      isEdit: false,
      updateIndex: null
    }
  } ,
  methods: {
    setDefault () {
      this.form = {
        name: '',
        age: 0
      }
    },
    add () {
    this.item.push(this.form)
    this.setDefault()
  },
    remove (index) {
      this.items.splice(index, 1)
    },
    setUpdate (item, index) {
      this.form.name = item.name
      this.form.age = item.age
      this.isEdit = true
      this.updateIndex = index
    },
    update () {
      this.items[this.updateIndex] = this.form
      this.setDefault()
      this.isEdit = false 
    }
  }
}
</script>

<style scoped>
  .table {
    font-family: Arial, Helvetica, sans-serif;
    border-collapse: collapse;
    width: 100%;
  } 

  .table td, .table th {
    border: 1px solid #ddd;
    padding: 8px;
  }

  .table tr:nth-child(even){background-color: #f2f2f2;}

  .table tr:hover {background-color: #ddd;}

  .table th {
    padding-top: 12px;
    padding-bottom: 12px;
    text-align: left;
    background-color: #0dcc06;
    color: white;
  }
</style>