<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- 里面写eleCalendar组件-->
            <ele-calendar
                  :render-content="renderContent"
                  :data="datedef"
                  :prop="prop"
                  @pick="myclick"
                  :border="true"
                  :lang="'en'"
                 
            ></ele-calendar>
  </div>
</template>

<script>
// @ is an alias to /src  
// :selectionMode="'dates'" 日期多选
import HelloWorld from '@/components/HelloWorld.vue'
import eleCalendar from 'ele-calendar'
import 'ele-calendar/dist/vue-calendar.css' //引入css
export default {
  name: 'home',
  data(){
    return{
      datedef:[
                    {"date":"2019-05-6","content":"内容","cid":null},
                    {"date":"2019-05-8","content":null,"cid":99},
                ],
      prop:'date' //对应日期字段名
    }
  },
  created(){},
  mounted(){},
  updated(){},
  components: {
    HelloWorld,
    eleCalendar
  },
  methods:{
     renderContent(h,parmas) {//设置lunarcalendar=true,parmas返回值包含农历 
            const loop = data =>{
               console.log(data.defvalue.value);
              return (
                data.defvalue.value ? (<div><div>{data.defvalue.text}</div> 
                <span  >0.2元</span>
                </div>) : <div>{data.defvalue.text}</div>
              )
           }
           return (
            <div  style="min-height:60px;">
             {loop(parmas)}
            </div>
            );
          //parmas返回当前日期和传入data对应内容
         },
      myclick(data,event,row,dome){
        //拿到当前的时间
       let youWant=data.getFullYear() + '-' + (data.getMonth() + 1) + '-' + data.getDate() + ' ' + data.getHours() + ':' + data.getMinutes() + ':' + data.getSeconds(); 
        alert(`${youWant} \n\ ${data}`);
        //Event 对象 事件通常与函数结合使用，函数不会在事件发生前被执行！
        console.log(event,"Event 对象");
        console.log(row,"row对象");
        console.log(dome,"dom对象")
      },
  }
}
</script>
<style>
  body{padding:0;margin:0 10px;}
  .title{padding:0;margin:10px 0;font:700 18px/1.5 \5fae\8f6f\96c5\9ed1;}
  .title em{font-style:normal;color:#C00;font-size:14px;}
  .title a{font:400 14px/1.5 Tahoma;}
  .example{margin-top:10px;}
  .example button{margin:0 5px 10px 0;}
</style>
