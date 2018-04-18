<template>
  <div id="app" class="container">
    <h2>Search for an Account Executive</h2>
    <div class="form">
      <input type="text"  maxlength="5" placeholder="Enter a 5 Digit ZipCode" ref="search_input" />
      <button type="submit" @click.prevent="getFormValue()">Search</button>
    </div>
    <hr>
    <modal v-show="isModalVisible" @close="closeModal" />

  </div>
</template>

<script>

import modal from '@/components/modal';

export default {
  name: 'Search',
  components: {
    modal,
  },
  data() {
    return {
      search: '',
      reps: [
        { id: '1',
          name: 'James Guy',
          phone: '555-555-5555',
          email: 'james@email.com',
          zipCodes: [
            '37209',
            '37205',
          ],
        },
        { id: '2',
          name: 'Jimmy Dean',
          phone: '555-555-5555',
          email: 'jimmy@email.com',
          zipCodes: [
            '37208',
          ],
        },
        { id: '3',
          name: 'Oscar Meyer',
          phone: '555-555-5555',
          email: 'oscar@email.com',
          zipCodes: [
            '37207',
          ],
        },
      ],
      isModalVisible: false,
    };
  },
  methods: {
    closeModal() {
      this.isModalVisible = false;
    },
    getFormValue() {
      const search = this.$refs.search_input.value;
      var i = 0;
      var j = 0;
      for ( i=0; i < this.reps.length; i++ ) {
        var rep = this.reps[i];
        for ( j=0; j < rep.zipCodes.length; j++ ) {
          var rep = rep;
          var zipCode = rep.zipCodes[j];
          if(zipCode == search) {
            var zipResult = rep;
            var found = true;
            break;
          }
        }
        if (found) {
          this.isModalVisible = true;
          document.getElementById('result').innerHTML = JSON.stringify(zipResult);
        }
        if (!found) {
          this.isModalVisible = true;
          document.getElementById('result').innerHTML = 'No sales rep found for this zipcode.';
        }
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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

input {
  height: 30px;
  line-height: 30px;
  padding: 5px 8px;
  font-size: 20px;
  border-radius: 8px;
  -webkit-border-radius: 8px;
  -moz-border-radius: 8px;
  border: 1px solid #ccc;
  box-shadow: none;
  -webkit-appearance: none;
}

button {
  box-shadow: none;
  -webkit-appearance: none;
  font-size: 18px;
  padding: 8px 20px;
  border-radius: 25px;
  background: orange;
  color: white;
  border: none;
  outline: none;
  transition: 0.3s ease;
}

button:hover {
  background: black;
  color: orange;
}

</style>
