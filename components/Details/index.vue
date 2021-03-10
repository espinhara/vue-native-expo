<template>
    <view>
      <!-- <text> Details</text> -->
      <image
          :style="{ width:'100%',  height:'90%', alignItems:'center'  }"
          :source="{ uri: navigation.getParam('imgSrcFull') }"
        />
      <button title="go back" :on-press="()=> navigation.goBack()"></button>
    </view>
</template>

<script>
    
export default {
    props:{
      navigation:{
        type:Object
      }
    }

}
</script>

<style>

</style>