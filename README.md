# vue-input-text-to-tags
A input component that can create tags for the result display
# install
	
	npm install vue-input-text-to-tags --save
	

# how to use
	template:
		 <text-to-tags :list="list" @change="handleCcChange"></text-to-tags>
	
	script:
		//import
		import TextToTags from 'vue-input-text-to-tags'
		//define
		components:{
			TextToTags
		},
		data(){
			return{
				list:['tag1','tag2']
			}
		}
		methods:{
			handleCcChange(list){
				console.log(list)

			}
		}
		
	
# props description
	list: defalut array for the component