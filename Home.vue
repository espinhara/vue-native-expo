<template>
  <view class="container">
     <text-input
        :style="{height: 40, width: 175, margin:50,  borderColor: 'gray', borderWidth: 1}"
        v-model="text"
      />
      <scroll-view :style="{ width:'100%' }">
        <view class="border" v-for="user in ResultSearch" :key="user.id">
          <touchable-opacity class="flex-container" :on-press="()=> handleListTap(user)">
            <image
              :style="{ width:60, height:60, borderRadius:60, marginRight:8 }"
              :source="{ uri: user.imgSrc }"
            />
            <text> {{ user.name }} </text>
          </touchable-opacity>
        </view>
      </scroll-view>
  </view>
</template>

<<script>
export default {
  props:{
    navigation:{
      type:Object
    }
  },
  // mounted() {
    
  // },
  data() {
    return {
      text:'',
      users:[
        {name:'espinhara', imgSrc:'https://avatars.githubusercontent.com/u/52253458?s=60&v=4',imgSrcFull:'https://avatars.githubusercontent.com/u/52253458?s=400&v=4', id:52253458},
        {name:'diego3g', imgSrc:'https://avatars.githubusercontent.com/u/2254731?s=60&v=4',imgSrcFull:'https://avatars.githubusercontent.com/u/2254731?s=400&v=4', id:2254731},
        {name:'EliasMurat', imgSrc:'https://avatars.githubusercontent.com/u/65032290?s=60&v=4',imgSrcFull:'https://avatars.githubusercontent.com/u/65032290?s=400&v=4', id:65032290},
        {name:'matheuslanduci', imgSrc:'https://avatars.githubusercontent.com/u/61356656?s=60&v=4',imgSrcFull:'https://avatars.githubusercontent.com/u/61356656?s=400&v=4', id:61356656},
        {name:'maykbrito', imgSrc:'https://avatars.githubusercontent.com/u/6643122?s=60&v=4',imgSrcFull:'https://avatars.githubusercontent.com/u/6643122?s=400&v=4', id:6643122},
        {name:'PowerKai', imgSrc:'https://avatars.githubusercontent.com/u/67343225?s=60&v=4',imgSrcFull:'https://avatars.githubusercontent.com/u/67343225?s=400&v=4', id:67343225},
      ]
    }
  },
  computed: {
    listFiltred(){
      let list = this.users;
      return list;
    },
    ResultSearch(){
      let searchFilter =[]
      searchFilter = this.listFiltred
      if(!searchFilter || searchFilter.length == 0){
        return []
      }
      if( !this.text ||this.text == '' || this.text == ' '){
        return searchFilter
      }else{
        return searchFilter.filter(
          (user)=> 
          user.name.includes(this.text)||
          user.name.toUpperCase().includes(this.text)||
          user.name.toLowerCase().includes(this.text)
        )
      }
    }
  },
  methods: {
    handleListTap(user){
      this.navigation.navigate('Details',{
        imgSrcFull: user.imgSrcFull
      })
    }
  },
}
</script>

<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}

.flex-container{
  flex-direction: row;
  align-items: center;
}
.border{
  border-bottom-width: 1;
  border-color: gray;
  width: 100%;
  padding: 10;
}
</style>
