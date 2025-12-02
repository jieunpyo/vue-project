<template>
    <div class="container">
        <div class="row">
            <div class="col-md-3" v-for="(vo,index) in food_list" :key="index">
                <div class="thumbnail">
                <a href="#">
                <img :src="vo.poster" style="width:240px;height: 150px">
                <div class="caption">
                    <p>{{vo.name}}</p>
                </div>
                </a>
            </div>
            </div>
        </div>
    </div>
</template> 
<script>
export default({
    // Model = 데이터 설정
    data(){
        return {
            food_list:[],
            curpage:1,
            totalpage:0,
            startPage:0,
            endPage:0
        }
    },
    // created - mounted - updated - unmounted
    // mounted = 다른 라이브러리 호환 (jquery,react)
    mounted(){
        // window.onload / $(function(){})
        this.dataRecv()
    },
    // 사용자 정의 메소드
    methods:{
        // 공통 사용 메소드 = 서버를 연결해서 데이터 읽기
        async dataRecv(){
            try{
                // 데이터 읽기
                const response=await fetch(
                    `http://localhost:8080/web/food/list_vue.do?page=${this.curpage}`
                )
                const result=await response.json()
                console.log(result)
                this.food_list=result.list
            }catch(error){
                console.log(error)
            }
        }
    }
})
</script>
<style>
.row {
    margin: 0px auto;
    width: 960px;
}
p{
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}
</style>
