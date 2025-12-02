<template>
    <div class="container">
        <div class="row">

        </div>
        <div class="row" style="margin-top:10px ;">

        </div>
        <div class="row text-center" style="margin-top:10px ;">

        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default({
    // HTML 제어
    data(){
        return {
            recipe_list:[], // List = [] , VO = {}
            curpage:1,
            totalpage:0,
            startPage:0,
            endPage:0,
            count:0
        }
    },
    mounted(){
        this.dataRecv()
    },
    methods:{
        // axios.post('url',null,{name:'',subject:''...})
        dataRecv(){
            axios.get('http://localhost:8080/web/recipe/list_vue.do',{
                params:{
                    page:this.curpage
                }
            }).then(response=>{
                console.log(response.data)
            })
        }
    }

})
</script>
<style>
p{
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}
.row {
    margin: 0px auto;
    width: 960px;
}
</style>