<!-- <template>
  <div class="big">
    <div class="orderHeader clear"><router-link to="/"><i></i>我的订单</router-link></div>
    <div class="orderMsg"><router-link to="/person"><i></i><span>个人信息</span><i></i></router-link></div>
    <div class="orderButton clear">
      <div class="active" @click="change">
      <p>{{init}}</p>
      <p>全部订单</p>
      </div>
      <div @click="change">
        <p>0</p>
        <p>待发货</p>
      </div>
      <div @click="change">
        <p>0</p>
        <p>已发货</p>
      </div>
      <div @click="change">
        <p>0</p>
        <p>已完成</p>
      </div>
    </div>

    <div class="orderList">
      <ul>
        <li><span>日期:</span><span></span></li>
        <li><span>订单号:</span><span></span></li>
        <li><span>状态:</span><span></span></li>
      </ul>
      <span class="orderListBtn" @click="orderShow">在线交谈</span>
      <span class="orderListBtn" @click="orderShow">退货</span>
      <span class="orderListBtn" @click="orderShow">评价</span>
    </div>
    <div class="orderList orderSend" style="display: none">
      <span>您目前还没有订单</span>
    </div>
    <div class="orderList orderHadSend" style="display:none">
      <span>您目前还没有订单</span>
    </div>
    <div class="orderList orderFinish" style="display:none">
      <ul>
        <li><span>日期:</span><span></span></li>
        <li><span>订单号:</span><span></span></li>
        <li><span>状态:</span><span></span></li>
      </ul>
      <span class="orderListBtn" @click="orderShow">在线交谈</span>
      <span class="orderListBtn" @click="orderShow">退货</span>
      <span class="orderListBtn" @click="orderShow">评价</span>
    </div>
  </div>
</template> -->

<script type="text/javascript">
  import '../css/public.css';
  import '../css/order.css';
  import $ from 'jquery'
  export default {
    name:'order',
    data:function(){
      return {}
    },
    methods:{
      orderShow:function(){
        alert('还未开通!')
      },
      change:function(e){
        if(!$(e.target).parent().hasClass('active')){
          $('.active').removeClass('active');
          $(e.target).parent().addClass('active');
          console.log($('.orderButton'))
        }
      }
    }
    }
</script>


 <template>
   <div class="big">
     <div class="orderHeader clear"><router-link to="/"><i></i>我的订单</router-link></div>
     <div class="orderMsg"><router-link to="/person"><i></i><span>个人信息</span><i></i></router-link></div>
     <div class="orderButton clear">
       <div class="active">
       <p>{{init}}</p>
       <p>全部订单</p>
       </div>
       <div>
         <p>0</p>
         <p>代发货</p>
       </div>
       <div>
         <p>0</p>
         <p>已发货</p>
       </div>
       <div>
         <p>0</p>
         <p>已完成</p>
       </div>
     </div>

     <div class="orderList">
       <ul>
         <li><span>日期:</span><span></span></li>
         <li><span>订单号:</span><span></span></li>
         <li><span>状态:已支付</span><span></span></li>
       </ul>
       <span class="orderListBtn" @click="orderShow">在线交谈</span>
       <span class="orderListBtn" @click="orderShow">退货</span>
       <span class="orderListBtn" @click="orderShow">评价</span>
     </div>
     <i></i>
   </div>
 </template>

 <script type="text/javascript">
   import '../css/public.css';
   import '../css/order.css'
   import $ from '../../js/jquery-3.1.1'
   import url from '../../../baseUrl.js'
   export default {
     name:'order',
     data:function(){
       return {
         init:0
       }
     },
     created:function(){
         var self=this;
         $.post(url.baseUrl+'php/goodscart.php',{'type':'order','username':window. localStorage.getItem("username")},function(res){
           var res=JSON.parse(res);
           for(var i=0;i<res.length;i++){
               self.init+=parseInt(res[i].num);//已完成订单全部数量
           }
           console.log(typeof res)
         })
     },
     methods:{
       orderShow:function(){
         alert('还未开通!')
       }
     }
     }
 </script>