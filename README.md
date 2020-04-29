# vue-input-text-to-tags
A input component that can create tags for the result display

<img src="https://user-images.githubusercontent.com/10140473/80558094-a83c0300-8a0b-11ea-9f18-f894ef2c2536.gif" alt="Coverage Status">

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