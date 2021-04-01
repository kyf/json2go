<template>
  <div class="hello">
  	<div class="left">
		<el-input @change="change" type="text" v-model="raw" />
	</div>
  	<div class="right">
		<el-input type="text" v-model="result" />
	</div>
  </div>
</template>

<script>
import Vue from 'vue';
import {Input, Message} from 'element-ui';

Vue.use(Input);
export default {
  name: 'Date',
  data () {
    return {
		raw: '',
		result: '',
    }
  },
  methods: {
	change (){
		try{
			let tmp = new Date(this.raw * 1000);
			this.result = tmp.toLocaleString(); 
		}catch(e){
			Message.error(e.toString());
		}
	},
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.hello{
		display:flex;
		flex-flow: row nowrap;
		justify-content: space-between;
	}
	.left, .right{
		width:49%;
	}
</style>
