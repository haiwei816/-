<template>
    <div id="background">
         <vue-particles color="#dedede"></vue-particles>
        <div id="name">
            智能宿舍分配平台
        </div>
            <el-card id="card" class="login">
            <div id="log" style="text-align: center">
                <el-input v-model="username" placeholder="请输入账号"></el-input><!--el输入框-->
                <el-input placeholder="请输入密码" v-model="password" show-password></el-input>
                <el-button type="primary" align="center">登录</el-button>
        </div>
            </el-card>
        <div id="clock">
                <div id="time">{{time}}</div>
                <div id="date">{{date}}</div>
        </div>
    </div>   
</template>
<style>
    #name {
        color: rgb(15, 34, 84);
        font-size: 25px;
        font-weight: 800;
        text-align: center;
        position: absolute;
        top: 20%;
        left: 43.5%;
    }

   #card {
    position: absolute;
    top:30%;
    left: 38%;
    width:352px;
    height: 262px;
    background-color: rgba(255, 255,255, 0.3);
}
    #background {
        position: fixed;
        height: 100%;
        width: 100%;
        top:0;
        left:0;
        background-image: linear-gradient(
            90deg,
            cyan,
            orange,
            purple
        );
        background-size: 400%;
        animation: myanimation 10s infinite;
    }
    #log{
        line-height: 62px;
    }
    @keyframes myanimation{
        0%{
            background-position: 0% 50%;
        }
        50%{
            background-position: 100% 50%;
        }
        100%{
            background-positon: 0% 50%;
        }
    }
    #clock {
        color:aliceblue;
        position: absolute;
        top: 70%;
        left: 75%;
        text-align: left;
}
    #time {
        font-size: 100px;
    }
    #date {
        font-size: 35px;
    }
</style>

<script>
export default{
    data(){
        return {
            username:"",
            password: "",
            time:"",
            date:"", 
        }
    },
    mounted(){
        this.$nextTick(()=>{
        setInterval(this.update_clock,1000);  
        })
    },
    methods:{
        update_clock:function(e){
            var d=new Date();
            var year=d.getFullYear();
            if(year<10){
            year="0"+year
            }
            var mon=d.getMonth();
            if(mon<10){
            mon="0"+mon
            }
            var day=d.getDate();
            if(day<10){
            day="0"+day    
            }
            var hour=d.getHours();
            if(hour<10){
            hour="0"+hour    
            }
            var minute=d.getMinutes();
            if(minute<10){
            minute=minute+"0"    
            }
            this.time=hour+":"+minute;
            this.date=year+"/"+mon+"/"+day;

        }
    }
}
</script>
