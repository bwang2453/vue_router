<template>
  <div >
    <h1>{{title}}</h1>
    <div class="columns is-multiline">
      <div class="column is-one-quarter" v-for="(data,index) in mrSites" :key="index">
        <img :src="data.image" class="img-fluid">
         <h3 @click="goTodetail(data.mrSiteId)" >{{data.mrSiteAbbrev}}</h3>
      </div>
    </div>
    <div> 
      <ul id="mr_site">
        <li v-for="(item, index) in mr_site" :key="index">
          {{ index }} : {{ item.abbrev }} - {{ item.name }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'home',
  data () {
    return {
      title: 'MR Sites',
      mr_site: [],
      mrSites:[
      {
        mrSiteAbbrev:"AHCH",
        image       : require('../assets/images/AHCH.jpg'),
        mrSiteId:1
      },
      {
        mrSiteAbbrev:"BAMBINO",
        image       : require('../assets/images/BAMBINO.png'),
        mrSiteId:2
      },
      {
        mrSiteAbbrev:"BICETRE",
        image       : require('../assets/images/BICETRE.png'),
        mrSiteId:3
      },
      {
        mrSiteAbbrev:"CEDARS",
        image       : require('../assets/images/CEDARS.png'),
        mrSiteId:4
      },
      {
        mrSiteAbbrev:"CHOP",
        image       : require('../assets/images/CHOP.png'),
        mrSiteId:5
      },
      {
        mrSiteAbbrev:"cnrs",
        image       : require('../assets/images/cnrs.png'),
        mrSiteId:6
      }
      ]
    }
  },

  mounted() {
    axios.get("https://internal.phhp.ufl.edu/idmd/qc_queue/a.php/mr_studies/list")
    .then(response => {
      this.mr_site = response.data;
    })
    .catch(error => {
      console.log(error);
    });
  },

  methods:{
    goTodetail(prodId) {
      let proId=prodId
      this.$router.push({name:'details',params:{Pid:proId}})
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.row img{
  max-height: 15em;
  width: 100%;

}
.row h3{
  cursor:pointer;
}
</style>
