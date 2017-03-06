<template>
  <div class="verify-box" >
    <div class="row">
      <input placeholder="请输入验证码" type="text" v-model="val">
      <div class="verify-img">
        <div class="zhao" @click.prevent="refresh"></div>
        <div v-for="item in data" :style=item.styleObj >{{item.value}}</div>
      </div>
    </div>
  </div>
</template>
<style>

  .verify-box input{
    outline: none;
    height: 36px;
    width: 80px;
    float: left;
    padding:0;
  }
  .verify-box  .row{
    overflow: hidden;
    margin:30px auto;
    width:170px;
  }
  .verify-img{
    float: left;
    height:40px;
    width:80px;
    background: #e4e4e4;
    color: #000;
    cursor: pointer;
    line-height:40px;
    position: relative;
    /*overflow: hidden;*/
  }
  .verify-img .zhao{
    position: absolute;
    width:100%;
    height:100%;
    z-index: 10;
    cursor: pointer;
    left:0;
    top:0;
  }
  .verify-img div{
    float: left;
    width:20px;
    height:40px;
    line-height:40px;
    text-align: center;
  }
  .verify-box .refresh{
    width:50px;
    height:40px;
    font-size:16px;
    box-sizing: border-box;
    border: 1px solid #000;
    color:#fff;
    float: left;
    background: green;
    margin-left:20px;
  }
</style>
<script type="text/babel">
  var valueArr = ['1','2','3','4','5','6','7','8','9','0','a','b','c','d','e','f','g','h','i','j','k'
    ,'l','m','n','o','p','q','r','s','t','u','v','w','x','v','z']
  export default{
    name : 'verify-box',
    data(){
      return {
        val : '',
        verify : false,
        data : [
          {
            value : valueArr [ Math.floor ( Math.random () * 36 ) ],
            styleObj : {
              transform : 'translateY(' + Math.floor ( ( Math.random() - 0.5) * 10 ) + 'px) scale('
              + ( Math.random() + 0.8 ) + ') rotate('
              + Math.floor( ( Math.random() - 0.5 ) * 100 ) + 'deg)'
            }
          },{
            value : valueArr [ Math.floor ( Math.random () * 36 ) ],
            styleObj : {
              transform : 'translateY(' + Math.floor ( ( Math.random() - 0.5) * 10 ) + 'px) scale('
              + ( Math.random() + 0.8 ) + ') rotate('
              + Math.floor( ( Math.random() - 0.5 ) * 100 ) + 'deg)'
            }
          },{
            value : valueArr [ Math.floor ( Math.random () * 36 ) ],
            styleObj : {
              transform : 'translateY(' + Math.floor ( ( Math.random() - 0.5) * 10 ) + 'px) scale('
              + ( Math.random() + 0.8 ) + ') rotate('
              + Math.floor( ( Math.random() - 0.5 ) * 100 ) + 'deg)'
            }
          }, {
            value : valueArr [ Math.floor ( Math.random () * 36 ) ],
            styleObj : {
              transform : 'translateY(' + Math.floor ( ( Math.random() - 0.5) * 10 ) + 'px) scale('
              + ( Math.random() + 0.8 ) + ') rotate('
              + Math.floor( ( Math.random() - 0.5 ) * 100 ) + 'deg)'
            }
          }
        ]
      }
    },
    computed : {
      answer : function () {
        let a = ''
        for ( let i = 0;i < this.data.length;i++) {
          a = a + this.data[i].value
        }
        return a
      }
    },
    methods : {
      refresh : function () {
        this.val = ''
        this.data = [
          {
            value: valueArr [Math.floor(Math.random() * 36)],
            styleObj: {
              transform: 'translateY(' + Math.floor(( Math.random() - 0.5) * 10) + 'px) scale('
              + ( Math.random() + 0.8 ) + ') rotate('
              + Math.floor(( Math.random() - 0.5 ) * 100) + 'deg)'
            }
          }, {
            value: valueArr [Math.floor(Math.random() * 36)],
            styleObj: {
              transform: 'translateY(' + Math.floor(( Math.random() - 0.5) * 10) + 'px) scale('
              + ( Math.random() + 0.8 ) + ') rotate('
              + Math.floor(( Math.random() - 0.5 ) * 100) + 'deg)'
            }
          }, {
            value: valueArr [Math.floor(Math.random() * 36)],
            styleObj: {
              transform: 'translateY(' + Math.floor(( Math.random() - 0.5) * 10) + 'px) scale('
              + ( Math.random() + 0.8 ) + ') rotate('
              + Math.floor(( Math.random() - 0.5 ) * 100) + 'deg)'
            }
          }, {
            value: valueArr [Math.floor(Math.random() * 36)],
            styleObj: {
              transform: 'translateY(' + Math.floor(( Math.random() - 0.5) * 10) + 'px) scale('
              + ( Math.random() + 0.8 ) + ') rotate('
              + Math.floor(( Math.random() - 0.5 ) * 100) + 'deg)'
            }
          }
        ]
      },
      submit : function () {
        if ( this.val === this.answer ){
          return Promise.resolve(this.val === this.answer)
        }else {
          return Promise.reject(this.val === this.answer)
        }
      }
    }
  }
</script>