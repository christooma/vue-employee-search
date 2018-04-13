<template>
  <div id="app" class="container">
    <h2>Zipcode Finder</h2>
    <div class="form">
      <input type="text"  maxlength="5" placeholder="ex: 94301" ref="search_input" />
      <input type="submit" @click.prevent="getFormValue()"/>
    </div>
    <div id="result"></div>
  </div>
</template>

<script>
export default {
  name: 'Search',
  data() {
    return {
      search: '',
      reps: [
        { id: '1',
          name: 'James Deboxtel',
          phone: '555-555-5555',
          email: 'james@enovate-medical.com',
          zipCodes: [
            '37209',
            '37205',
          ],
        },
        { id: '2',
          name: 'Jimmy Dean',
          phone: '555-555-5555',
          email: 'jimmy@enovate-medical.com',
          zipCodes: [
            '37208',
          ],
        },
        { id: '3',
          name: 'Oscar Meyer',
          phone: '555-555-5555',
          email: 'oscar@enovate-medical.com',
          zipCodes: [
            '37207',
          ],
        },
      ],
    };
  },
  methods: {
    getFormValue() {
      var search = this.$refs.search_input.value;
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
        if(found) {
            document.getElementById("result").innerHTML = JSON.stringify(zipResult);
        }
        if(!found) {
          document.getElementById("result").innerHTML = 'No sales rep found for this zipcode.';
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
</style>
