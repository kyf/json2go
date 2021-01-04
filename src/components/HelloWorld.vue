<template>
  <div class="hello">
  	<div class="left">
		<el-input rows="30" @change="change" type="textarea" v-model="raw" />
	</div>
  	<div class="right">
		<el-input rows="30" type="textarea" v-model="result" />
	</div>
  </div>
</template>

<script>
import Vue from 'vue';
import {Input} from 'element-ui';
import {jsonToGo} from '../util/json-to-go';

Vue.use(Input);
export default {
  name: 'HelloWorld',
  data () {
    return {
		raw: '',
		result: '',
    }
  },
  methods: {
	change (){
		let tmp = jsonToGo(this.raw);
		this.result = tmp.go == '' ? tmp.error : tmp.go; 
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
