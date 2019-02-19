<template>
    <div>
        <label>请输入要查找的图书类型:</label><input v-model="bookType"/>
        <button @click="sendajax">发送请求</button>
         <ul>
             <li v-for="(item,index) in lists" :key="item.id" :class="bookType">{{item.title}}</li>
         </ul>
    </div>
   
</template>
<script>
export default {
    name:'ajaxrequest',
    data(){
        return {
            lists:[],
            bookType:""
        }
    },
    methods:{
        sendajax(){
            console.log(this.bookType)
            this.$http.get(' http://localhost:3000/'+this.bookType,{
                "id": 1,
                "title": "json-server",
                "author": "type"
    
            }).then((res)=>{
                this.lists=res.data;
                console.log(res.data);
            });
    }
}
}
</script>

<style>
    .chinese {
        color:darkblue;
    }
    .math{
        color:aquamarine;

    }
    .english{
        color:darkmagenta;
    }
</style>
