<template>
  <div>
    <div class='zuoye'>
      <h3>案例1:帅哥美女走一走</h3>
      <ul>
        <li v-for="(item ,index) in list01" :key="index">{{item}}</li>
      </ul>
      <button @click="change">走一走</button>
    </div>



    <div class='zuoye'>
      <h3>案例2:加加减减</h3>
      <ul>
        <li v-for="(item ,index) in list02" :key='index'>{{item}}<button @click="removeThis(index)">删除</button></li>
      </ul>
      <button @click="addbutton">生成</button>
    </div>



    <div class='zuoye app'>
      <h3>案例3:购物车</h3>
          <table class="tb">
      <tr>
        <th>编号</th>
        <th>品牌名称</th>
        <th>创立时间</th>
        <th>操作</th>
      </tr>
      <!-- 循环渲染的元素tr -->
      <tr v-for="item in list03" :key="item.id">
        <td>{{item.id}}</td>
        <td>{{item.name}}</td>
        <td>{{item.time}}</td>
        <td>
          <button @click='deleteThis(index)'>删除</button>
        </td>
      </tr>
      <tr>
        <td colspan="4" v-show="!list03.length">没有数据咯~</td>
      </tr>
    </table>
    </div>


    <div class='zuoye'>
      <h3>案例4:逛水果店</h3>
      <h5>欢迎光临vue开发的收银系统--水果店</h5>
      <p>苹果{{fruitprice}}￥/斤,折扣{{fruitzhekou}}折</p>
      <p>请输入购买数量 <input type="text" v-model="fruitnum"> </p>
      <p><button @click="jiezhang">结账买单</button></p>
      <p>结账单:总价{{zongprice}}￥元 折后价{{zheprice}}￥元 优惠了{{shengprice}}￥元</p>
    </div>



    <div class='zuoye'>
      <h3>案例5:选择你喜欢的</h3>
      <span v-for='(item,index) in list05' :key="index">  <input type="checkbox" :value="item" v-model="loves">{{item}} </span>
      <ul>
        <li v-for='(item,index) in loves' :key="index">{{item}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {

  data(){

    return{
      loves:[],
      fruitprice:'8',
      fruitzhekou:'8',
      fruitnum:'',
      zongprice:'0',
      zheprice:'0',
      shengprice:'0',
      list01:['美女','帅哥','程序员'],
      list02:[],
      list03: [
        { id: 1, name: "奔驰", time: "2020-08-01" },
        { id: 2, name: "宝马", time: "2020-08-02" },
        { id: 3, name: "奥迪", time: "2020-08-03" },
      ],
      list05:["科幻", "喜剧", "动漫", "冒险", "科技", "军事", "娱乐", "奇闻"]
    }
  },
  methods:{
    change(){
      //将第一个删了  加到最后
      this.list01.push(this.list01.shift())
    },
    addbutton(){
      this.list02.push(Math.floor(Math.random() * (100) + 1))
    },
    removeThis(index){
      console.log(index);
      this.list02.splice(index,1)
    },
    deleteThis(index){
      this.list03.splice(index,1)
    },
    jiezhang(){
      this.zongprice=(this.fruitnum*this.fruitprice).toFixed(2)
      this.zheprice=(this.zongprice*this.fruitzhekou/10).toFixed(2)
      this.shengprice=(this.zongprice-this.zheprice).toFixed(2)
    }
  }
}
</script>

<style>
.zuoye{
  width: 500px;
  margin:20px;
  /* height: 400px; */
  border: 2px solid #000;
  border-radius: 15px;
  padding: 15px;
}
 .app{
  width: 600px;
  /* margin: 10px auto; */
}

.tb {
  border-collapse: collapse;
  width: 100%;
}

.tb th {
  background-color: #0094ff;
  color: white;
}

.tb td,
.tb th {
  padding: 5px;
  border: 1px solid black;
  text-align: center;
}

.add {
  padding: 5px;
  border: 1px solid black;
  margin-bottom: 10px;
}
</style>
