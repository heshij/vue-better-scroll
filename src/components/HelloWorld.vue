<template>
    <div class="hello">
        <div class="main">
            <div class="wrapper" ref="wrapper">
                <div class="content" ref="tabcontent" >
                    <ul>
                        <li v-for="(item,index) of TabList" :key="index" ref="tabitem">
                            {{item}}
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import BScroll from 'better-scroll'
    export default {
        name: 'HelloWorld',
        data(){
            return{
                TabList:[
                    "111111",
                    "222222",
                    "3333333",
                    "4444444",
                    "5555555",
                    "66666666",
                    "777777",
                    "888888",
                    "999999",
                    "222222",
                    "111111",
                    "222222",
                    "3333333",
                    "4444444",
                    "5555555",
                    "66666666",
                    "777777",
                    "888888",
                    "999999",
                    "222222",
                ]
            }
        },
        mounted() {
            //即定时器 20ms

            this.$nextTick(() => {
                let width=0;
                for (let  i = 0; i <this.TabList.length; i++) {
                    width+=this.$refs.tabitem[0].getBoundingClientRect().width
                }
                this.$refs.tabcontent.style.width=width+'px';                //$refs绑定元素
                this.$nextTick(()=>{
                    if(!this.scroll){
                        this.scroll = new BScroll(this.$refs.wrapper, {
                            //开启点击事件 默认为false
                            click:true,
                            startX:0,
                            scrollX:true,
                            eventPassthrough:'vertical'
                        })
                        // console.log(this.scroll)
                    }else{
                        this.scroll.refresh()
                    }
                })
            })
        }

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .hello {
        width: 750px;
        height: auto;
    }
    .wrapper{
        width: 100%;
        position:absolute;
        top: 45px;
        bottom: 50px;
        overflow: hidden;
        z-index: 1;
        background-color: skyblue;
    }
    .content{
        height:100%;
    }
    .content ul{
        width: 100%;
        height: auto;
        display: flex;
        justify-content: space-between;
    }
    .content ul li{
        height: 60px;
        line-height: 60px;
        text-align: center;
        border: 1px solid red;
        margin: 0 20px;
        list-style: none;
    }
</style>
