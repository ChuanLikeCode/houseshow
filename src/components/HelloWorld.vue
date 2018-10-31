<template>
  <div >
    <div  style="background-color: #001a3d;height: 50px; text-align:center;color: white;font-size: 32px;" >
        爬取贝壳网实现各城市二手房统计图
      <!--<i class="fa fa-square-o"></i><font color="#fff">-->
      <!--<button type="button" id="send_message" @click="sendMessage">发送 message</button>-->
      <!--<button type="button" id="close_websocket" @click = closeConnect>关闭 websocket</button>-->
    </div>
    <div>
      <div id="areaBarChart" :style="{marginRight:'50px',width: '600px', height: '800px',float:'right'}"></div>
      <div id="HistoricalTransactionRecordChart" :style="{marginTop:'50px',marginLeft:'50px',width: '600px', height: '800px'}"></div>
    </div>
    <div>
      <div id="priceBarChart" :style="{margin:'50px',width: '600px', height: '800px'}"></div>
      <!--<div id="dataTimeBarChart" :style="{marginTop:'50px',marginLeft:'50px',width: '600px', height: '800px'}"></div>-->
    </div>
    <!--// shanghai:[],dongguan:[],zhongshan:[],foshan:[],nanjin:[],xiamen:[],-->
    <!--//   hefei:[],dalian:[],tianjin:[],guangzhou:[],langfang:[],huizhou:[],-->
    <!--//   chengdu:[],hangzhou:[],wuhan:[],shengyang:[],jinan:[],haikou:[],-->
    <!--//   shengzhen:[],yantai:[],shijiazhuang:[],suzhou:[],xian:[],chongqin:[],-->
    <!--//   changsha:[],qingdao:[],beijin:[],-->
    <div id="beijin" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="shanghai" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="dongguan" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="zhongshan" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="foshan" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="nanjin" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="xiamen" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="hefei" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="dalian" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="tianjin" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="guangzhou" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="langfang" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="huizhou" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="chengdu" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="hangzhou" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="wuhan" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="shengyang" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="jinan" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="haikou" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="shengzhen" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="yantai" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="shijiazhuang" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="suzhou" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="xian" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="chongqin" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="changsha" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>
    <div id="qingdao" :style="{width: '1300px', height: '500px',margin:'0px auto'}"></div>



  </div>

</template>

<script>

  import { beijin } from  '../assets/js/北京.js'
  import { shanghai } from  '../assets/js/上海.js'
  import { dongguan } from  '../assets/js/东莞.js'
  import { zhongshan } from  '../assets/js/中山.js'
  import { foshan } from  '../assets/js/佛山.js'
  import { nanjin } from  '../assets/js/南京.js'
  import { xiamen } from  '../assets/js/厦门.js'
  import { hefei } from  '../assets/js/合肥.js'
  import { dalian } from  '../assets/js/大连.js'
  import { tianjin } from  '../assets/js/天津.js'
  import { guangzhou } from  '../assets/js/广州.js'
  import { langfang } from  '../assets/js/廊坊.js'
  import { huizhou } from  '../assets/js/惠州.js'
  import { chengdu } from  '../assets/js/成都.js'
  import { hangzhou } from  '../assets/js/杭州.js'
  import { wuhan } from  '../assets/js/武汉.js'
  import { shengyang } from  '../assets/js/沈阳.js'
  import { jinan } from  '../assets/js/济南.js'
  import { haikou } from  '../assets/js/海口.js'
  import { shengzhen } from  '../assets/js/深圳.js'
  import { yantai } from  '../assets/js/烟台.js'
  import { shijiazhuang } from  '../assets/js/石家庄.js'
  import { suzhou } from  '../assets/js/苏州.js'
  import { xian } from  '../assets/js/西安.js'
  import { chongqin } from  '../assets/js/重庆.js'
  import { changsha } from  '../assets/js/长沙.js'
  import { qingdao } from  '../assets/js/青岛.js'
  import { beijincount } from  '../assets/jscount/北京count.js'
  import { shanghaicount } from  '../assets/jscount/上海count.js'
  import { dongguancount } from  '../assets/jscount/东莞count.js'
  import { zhongshancount } from  '../assets/jscount/中山count.js'
  import { foshancount } from  '../assets/jscount/佛山count.js'
  import { nanjincount } from  '../assets/jscount/南京count.js'
  import { xiamencount } from  '../assets/jscount/厦门count.js'
  import { hefeicount } from  '../assets/jscount/合肥count.js'
  import { daliancount } from  '../assets/jscount/大连count.js'
  import { tianjincount } from  '../assets/jscount/天津count.js'
  import { guangzhoucount } from  '../assets/jscount/广州count.js'
  import { langfangcount } from  '../assets/jscount/廊坊count.js'
  import { huizhoucount } from  '../assets/jscount/惠州count.js'
  import { chengducount } from  '../assets/jscount/成都count.js'
  import { hangzhoucount } from  '../assets/jscount/杭州count.js'
  import { wuhancount } from  '../assets/jscount/武汉count.js'
  import { shengyangcount } from  '../assets/jscount/沈阳count.js'
  import { jinancount } from  '../assets/jscount/济南count.js'
  import { haikoucount } from  '../assets/jscount/海口count.js'
  import { shengzhencount } from  '../assets/jscount/深圳count.js'
  import { yantaicount } from  '../assets/jscount/烟台count.js'
  import { shijiazhuangcount } from  '../assets/jscount/石家庄count.js'
  import { suzhoucount } from  '../assets/jscount/苏州count.js'
  import { xiancount } from  '../assets/jscount/西安count.js'
  import { chongqincount } from  '../assets/jscount/重庆count.js'
  import { changshacount } from  '../assets/jscount/长沙count.js'
  import { qingdaocount } from  '../assets/jscount/青岛count.js'

export default {
  name: 'HelloWorld',
  // data: ["上海","东莞","中山","佛山","南京","厦门",
  //   "合肥","大连","天津","广州","廊坊","惠州",
  //   "成都","杭州","武汉","沈阳","济南","海口",
  //   "深圳","烟台","石家庄","苏州","西安","重庆","长沙","青岛"]
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      drawingName:['建筑面积:平方米','历史成交记录:万元','单价: 元/平方','房屋朝向'],
      theCharts:{
      beijin:'',shanghai:'',dongguan:'',zhongshan:'',foshan:'',nanjin:'',xiamen:'',
        hefei:'',dalian:'',tianjin:'',guangzhou:'',langfang:'',huizhou:'',
        chengdu:'',hangzhou:'',wuhan:'',shengyang:'',jinan:'',haikou:'',
        shengzhen:'',yantai:'',shijiazhuang:'',suzhou:'',xian:'',chongqin:'',
        changsha:'',qingdao:''
      },
      theData:[ beijincount,shanghaicount,dongguancount,zhongshancount,foshancount,nanjincount,xiamencount,
      hefeicount,daliancount,tianjincount,guangzhoucount,langfangcount,huizhoucount,
      chengducount,hangzhoucount,wuhancount,shengyangcount,jinancount,haikoucount,
      shengzhencount,yantaicount,shijiazhuangcount,suzhoucount,xiancount,chongqincount,
      changshacount,qingdaocount],
      theId:['beijin','shanghai','dongguan','zhongshan','foshan','nanjin','xiamen',
        'hefei','dalian','tianjin','guangzhou','langfang','huizhou',
        'chengdu','hangzhou','wuhan','shengyang','jinan','haikou',
        'shengzhen','yantai','shijiazhuang','suzhou','xian','chongqin',
        'changsha','qingdao'],
      theName:["北京","上海","东莞","中山","佛山","南京","厦门",
          "合肥","大连","天津","广州","廊坊","惠州",
          "成都","杭州","武汉","沈阳","济南","海口",
          "深圳","烟台","石家庄","苏州","西安","重庆","长沙","青岛"],
      areaBarChart: "",
      areaBarChartData:[beijin[11].mean,shanghai[11].mean,dongguan[11].mean,zhongshan[11].mean,foshan[11].mean,nanjin[11].mean,xiamen[11].mean,hefei[11].mean,dalian[11].mean,
        tianjin[11].mean,guangzhou[11].mean,langfang[11].mean,huizhou[11].mean,chengdu[11].mean,hangzhou[11].mean,wuhan[11].mean,shengyang[11].mean,jinan[11].mean,haikou[11].mean,
        shengzhen[11].mean,yantai[11].mean,shijiazhuang[11].mean,suzhou[11].mean,xian[11].mean,chongqin[11].mean,changsha[11].mean,qingdao[11].mean],
      HistoricalTransactionRecordChart:"",
      HistoricalTransactionRecordChartData:[beijin[12].mean,shanghai[12].mean,dongguan[12].mean,zhongshan[12].mean,foshan[12].mean,nanjin[12].mean,xiamen[12].mean,hefei[12].mean,dalian[12].mean,
        tianjin[12].mean,guangzhou[12].mean,langfang[12].mean,huizhou[12].mean,chengdu[12].mean,hangzhou[12].mean,wuhan[12].mean,shengyang[12].mean,jinan[12].mean,haikou[12].mean,
        shengzhen[12].mean,yantai[12].mean,shijiazhuang[12].mean,suzhou[12].mean,xian[12].mean,chongqin[12].mean,changsha[12].mean,qingdao[12].mean],
      priceBarChart:"",
      priceBarChartData:[beijin[13].mean,shanghai[13].mean,dongguan[13].mean,zhongshan[13].mean,foshan[13].mean,nanjin[13].mean,xiamen[13].mean,hefei[13].mean,dalian[13].mean,
        tianjin[13].mean,guangzhou[13].mean,langfang[13].mean,huizhou[13].mean,chengdu[13].mean,hangzhou[13].mean,wuhan[13].mean,shengyang[13].mean,jinan[13].mean,haikou[13].mean,
        shengzhen[13].mean,yantai[13].mean,shijiazhuang[13].mean,suzhou[13].mean,xian[13].mean,chongqin[13].mean,changsha[13].mean,qingdao[13].mean],
      dataTimeBarChart:"",
      dataTimeBarChartData:[beijin[11].mean,shanghai[11].mean,dongguan[11].mean,zhongshan[11].mean,foshan[11].mean,nanjin[11].mean,xiamen[11].mean,hefei[11].mean,dalian[11].mean,
        tianjin[11].mean,guangzhou[11].mean,langfang[11].mean,huizhou[11].mean,chengdu[11].mean,hangzhou[11].mean,wuhan[11].mean,shengyang[11].mean,jinan[11].mean,haikou[11].mean,
        shengzhen[11].mean,yantai[11].mean,shijiazhuang[11].mean,suzhou[11].mean,xian[11].mean,chongqin[11].mean,changsha[11].mean,qingdao[11].mean],
      theHisPrice:[{'name':'北京','value':beijin[12].mean},{'name':'上海','value':shanghai[12].mean},{'name':'东莞','value':dongguan[12].mean},{'name':'中山','value':zhongshan[12].mean},{'name':'佛山','value':foshan[12].mean},{'name':'南京','value':nanjin[12].mean},{'name':'厦门','value':xiamen[12].mean},{'name':'合肥','value':hefei[12].mean},{'name':'大连','value':dalian[12].mean},{'name':'天津','value':
        tianjin[12].mean},{'name':'广州','value':guangzhou[12].mean},{'name':'廊坊','value':langfang[12].mean},{'name':'惠州','value':huizhou[12].mean},{'name':'成都','value':chengdu[12].mean},{'name':'杭州','value':hangzhou[12].mean},{'name':'武汉','value':wuhan[12].mean},{'name':'沈阳','value':shengyang[12].mean},{'name':'济南','value':jinan[12].mean},{'name':'海口','value':haikou[12].mean},{'name':'深圳','value':
        shengzhen[12].mean},{'name':'烟台','value':yantai[12].mean},{'name':'石家庄','value':shijiazhuang[12].mean},{'name':'苏州','value':suzhou[12].mean},{'name':'西安','value':xian[12].mean},{'name':'重庆','value':chongqin[12].mean},{'name':'长沙','value':changsha[12].mean},{'name':'青岛','value':qingdao[12].mean}],
      thePrice:[{'name':'北京','value':beijin[13].mean},{'name':'上海','value':shanghai[13].mean},{'name':'东莞','value':dongguan[13].mean},{'name':'中山','value':zhongshan[13].mean},{'name':'佛山','value':foshan[13].mean},{'name':'南京','value':nanjin[13].mean},{'name':'厦门','value':xiamen[13].mean},{'name':'合肥','value':hefei[13].mean},{'name':'大连','value':dalian[13].mean},{'name':'天津','value':
      tianjin[13].mean},{'name':'广州','value':guangzhou[13].mean},{'name':'廊坊','value':langfang[13].mean},{'name':'惠州','value':huizhou[13].mean},{'name':'成都','value':chengdu[13].mean},{'name':'杭州','value':hangzhou[13].mean},{'name':'武汉','value':wuhan[13].mean},{'name':'沈阳','value':shengyang[13].mean},{'name':'济南','value':jinan[13].mean},{'name':'海口','value':haikou[13].mean},{'name':'深圳','value':
      shengzhen[13].mean},{'name':'烟台','value':yantai[13].mean},{'name':'石家庄','value':shijiazhuang[13].mean},{'name':'苏州','value':suzhou[13].mean},{'name':'西安','value':xian[13].mean},{'name':'重庆','value':chongqin[13].mean},{'name':'长沙','value':changsha[13].mean},{'name':'青岛','value':qingdao[13].mean}],
     theArea:[{'name':'北京','value':beijin[11].mean},{'name':'上海','value':shanghai[11].mean},{'name':'东莞','value':dongguan[11].mean},{'name':'中山','value':zhongshan[11].mean},{'name':'佛山','value':foshan[11].mean},{'name':'南京','value':nanjin[11].mean},{'name':'厦门','value':xiamen[11].mean},{'name':'合肥','value':hefei[11].mean},{'name':'大连','value':dalian[11].mean},{'name':'天津','value':
        tianjin[11].mean},{'name':'广州','value':guangzhou[11].mean},{'name':'廊坊','value':langfang[11].mean},{'name':'惠州','value':huizhou[11].mean},{'name':'成都','value':chengdu[11].mean},{'name':'杭州','value':hangzhou[11].mean},{'name':'武汉','value':wuhan[11].mean},{'name':'沈阳','value':shengyang[11].mean},{'name':'济南','value':jinan[11].mean},{'name':'海口','value':haikou[11].mean},{'name':'深圳','value':
        shengzhen[11].mean},{'name':'烟台','value':yantai[11].mean},{'name':'石家庄','value':shijiazhuang[11].mean},{'name':'苏州','value':suzhou[11].mean},{'name':'西安','value':xian[11].mean},{'name':'重庆','value':chongqin[11].mean},{'name':'长沙','value':changsha[11].mean},{'name':'青岛','value':qingdao[11].mean}],

    }
  },
  mounted(){
    // this.loadsData();
    // 画图
    this.drawArea();

  },
  computed:{
    theSortPrice:function () {
      return this.thePrice.sort(function (a,b) {
          return a.value - b.value;
      });
    },
    theSortArea:function () {
      return this.theArea.sort(function (a,b) {
        return a.value - b.value;
      });
    },
    theSortHisPrice:function () {
      return this.theHisPrice.sort(function (a,b) {
        return a.value - b.value;
      });
    }
  },
  methods:{
      loadsData() {
        // this.areaBarChart=
        // console.log(shanghai[12].mean)
      },
      drawArea(){
        // 基于准备好的dom，初始化echarts实例HistoricalTransactionRecordChart
        var beijinChart = this.$echarts.init(document.getElementById('beijin'));
        var shanghaiChart = this.$echarts.init(document.getElementById('shanghai'));
        var dongguanChart = this.$echarts.init(document.getElementById('dongguan'));
        var zhongshanChart = this.$echarts.init(document.getElementById('zhongshan'));
        var foshanChart = this.$echarts.init(document.getElementById('foshan'));
        var nanjinChart = this.$echarts.init(document.getElementById('nanjin'));
        var xiamenChart = this.$echarts.init(document.getElementById('xiamen'));
        var hefeiChart = this.$echarts.init(document.getElementById('hefei'));
        var dalianChart = this.$echarts.init(document.getElementById('dalian'));
        var tianjinChart = this.$echarts.init(document.getElementById('tianjin'));
        var guangzhouChart = this.$echarts.init(document.getElementById('guangzhou'));
        var langfangChart = this.$echarts.init(document.getElementById('langfang'));
        var huizhouChart = this.$echarts.init(document.getElementById('huizhou'));
        var chengduChart = this.$echarts.init(document.getElementById('chengdu'));
        var hangzhouChart = this.$echarts.init(document.getElementById('hangzhou'));
        var wuhancChart = this.$echarts.init(document.getElementById('wuhan'));
        var shengyangChart = this.$echarts.init(document.getElementById('shengyang'));
        var jinanChart = this.$echarts.init(document.getElementById('jinan'));
        var haikouChart = this.$echarts.init(document.getElementById('haikou'));
        var shengzhenChart = this.$echarts.init(document.getElementById('shengzhen'));
        var yantaiChart = this.$echarts.init(document.getElementById('yantai'));
        var shijiazhuangChart = this.$echarts.init(document.getElementById('shijiazhuang'));
        var suzhouChart = this.$echarts.init(document.getElementById('suzhou'));
        var xianChart = this.$echarts.init(document.getElementById('xian'));
        var chongqinChart = this.$echarts.init(document.getElementById('chongqin'));
        var changshaChart = this.$echarts.init(document.getElementById('changsha'));
        var qingdaoChart = this.$echarts.init(document.getElementById('qingdao'));
        this.areaBarChart = this.$echarts.init(document.getElementById('areaBarChart'));
        this.HistoricalTransactionRecordChart = this.$echarts.init(document.getElementById('HistoricalTransactionRecordChart'));
        this.priceBarChart = this.$echarts.init(document.getElementById('priceBarChart'));
        // this.dataTimeBarChart = this.$echarts.init(document.getElementById('dataTimeBarChart'));
        this.setBarOption(this.areaBarChart,0,this.theSortArea,'各城市二手成交房屋建筑面积均值')
        this.setBarOption(this.HistoricalTransactionRecordChart,1,this.theSortHisPrice,'各城市二手成交房屋价格均值')
        this.setBarOption(this.priceBarChart,2,this.theSortPrice,'各城市二手成交房屋单价均值')

        this.setoptinManyLin(beijinChart,'北京二手房单价、成交额、建筑面积走势图',beijincount.单价,beijincount.历史成交记录,beijincount.建筑面积,beijincount.成交时间)
        this.setoptinManyLin(shanghaiChart,'上海二手房单价、成交额、建筑面积走势图',shanghaicount.单价,shanghaicount.历史成交记录,shanghaicount.建筑面积,shanghaicount.成交时间)
        this.setoptinManyLin(dongguanChart,'东莞二手房单价、成交额、建筑面积走势图',dongguancount.单价,dongguancount.历史成交记录,dongguancount.建筑面积,dongguancount.成交时间)
        this.setoptinManyLin(zhongshanChart,'中山二手房单价、成交额、建筑面积走势图',zhongshancount.单价,zhongshancount.历史成交记录,zhongshancount.建筑面积,zhongshancount.成交时间)
        this.setoptinManyLin(foshanChart,'佛山二手房单价、成交额、建筑面积走势图',foshancount.单价,foshancount.历史成交记录,foshancount.建筑面积,foshancount.成交时间)
        this.setoptinManyLin(nanjinChart,'南京二手房单价、成交额、建筑面积走势图',nanjincount.单价,nanjincount.历史成交记录,nanjincount.建筑面积,nanjincount.成交时间)
        this.setoptinManyLin(xiamenChart,'厦门二手房单价、成交额、建筑面积走势图',xiamencount.单价,xiamencount.历史成交记录,xiamencount.建筑面积,xiamencount.成交时间)
        this.setoptinManyLin(hefeiChart,'合肥二手房单价、成交额、建筑面积走势图',hefeicount.单价,hefeicount.历史成交记录,hefeicount.建筑面积,hefeicount.成交时间)
        this.setoptinManyLin(dalianChart,'大连二手房单价、成交额、建筑面积走势图',daliancount.单价,daliancount.历史成交记录,daliancount.建筑面积,daliancount.成交时间)
        this.setoptinManyLin(tianjinChart,'天津二手房单价、成交额、建筑面积走势图',tianjincount.单价,tianjincount.历史成交记录,tianjincount.建筑面积,tianjincount.成交时间)
        this.setoptinManyLin(guangzhouChart,'广州二手房单价、成交额、建筑面积走势图',guangzhoucount.单价,guangzhoucount.历史成交记录,guangzhoucount.建筑面积,guangzhoucount.成交时间)
        this.setoptinManyLin(langfangChart,'廊坊二手房单价、成交额、建筑面积走势图',langfangcount.单价,langfangcount.历史成交记录,langfangcount.建筑面积,langfangcount.成交时间)
        this.setoptinManyLin(huizhouChart,'惠州二手房单价、成交额、建筑面积走势图',huizhoucount.单价,huizhoucount.历史成交记录,huizhoucount.建筑面积,huizhoucount.成交时间)
        this.setoptinManyLin(chengduChart,'成都二手房单价、成交额、建筑面积走势图',chengducount.单价,chengducount.历史成交记录,chengducount.建筑面积,chengducount.成交时间)
        this.setoptinManyLin(hangzhouChart,'杭州二手房单价、成交额、建筑面积走势图',hangzhoucount.单价,hangzhoucount.历史成交记录,hangzhoucount.建筑面积,hangzhoucount.成交时间)
        this.setoptinManyLin(wuhancChart,'武汉二手房单价、成交额、建筑面积走势图',wuhancount.单价,wuhancount.历史成交记录,wuhancount.建筑面积,wuhancount.成交时间)
        this.setoptinManyLin(shengyangChart,'沈阳二手房单价、成交额、建筑面积走势图',shengyangcount.单价,shengyangcount.历史成交记录,shengyangcount.建筑面积,shengyangcount.成交时间)
        this.setoptinManyLin(jinanChart,'济南二手房单价、成交额、建筑面积走势图',jinancount.单价,jinancount.历史成交记录,jinancount.建筑面积,jinancount.成交时间)
        this.setoptinManyLin(haikouChart,'海口二手房单价、成交额、建筑面积走势图',haikoucount.单价,haikoucount.历史成交记录,haikoucount.建筑面积,haikoucount.成交时间)
        this.setoptinManyLin(shengzhenChart,'深圳二手房单价、成交额、建筑面积走势图',shengzhencount.单价,shengzhencount.历史成交记录,shengzhencount.建筑面积,shengzhencount.成交时间)
        this.setoptinManyLin(yantaiChart,'烟台二手房单价、成交额、建筑面积走势图',yantaicount.单价,yantaicount.历史成交记录,yantaicount.建筑面积,yantaicount.成交时间)
        this.setoptinManyLin(shijiazhuangChart,'石家庄二手房单价、成交额、建筑面积走势图',shijiazhuangcount.单价,shijiazhuangcount.历史成交记录,shijiazhuangcount.建筑面积,shijiazhuangcount.成交时间)
        this.setoptinManyLin(suzhouChart,'苏州二手房单价、成交额、建筑面积走势图',suzhoucount.单价,suzhoucount.历史成交记录,suzhoucount.建筑面积,suzhoucount.成交时间)
        this.setoptinManyLin(xianChart,'西安二手房单价、成交额、建筑面积走势图',xiancount.单价,xiancount.历史成交记录,xiancount.建筑面积,xiancount.成交时间)
        this.setoptinManyLin(chongqinChart,'重庆二手房单价、成交额、建筑面积走势图',chongqincount.单价,chongqincount.历史成交记录,chongqincount.建筑面积,chongqincount.成交时间)
        this.setoptinManyLin(changshaChart,'长沙二手房单价、成交额、建筑面积走势图',changshacount.单价,changshacount.历史成交记录,changshacount.建筑面积,changshacount.成交时间)
        this.setoptinManyLin(qingdaoChart,'青岛二手房单价、成交额、建筑面积走势图',qingdaocount.单价,qingdaocount.历史成交记录,qingdaocount.建筑面积,qingdaocount.成交时间)
      },
      setBarOption(drawChartId,index,data,title){
        var myColor=["#ffd200","#00eaff","#0866e5","#1d9bff","#29c729","#ff8400",'#e4393c','#e63810','#ff6b00','#e3b61f','#13b5b1'];
        var option = {
          backgroundColor: '#394056',
          title:{
            text:title,
            left:'left',
            textStyle: {
              color: '#fff',
            },
          },
          legend: {
            top: 30,
            left:30,
            textStyle: {
              color: '#fff',
            },
            data: [this.drawingName[index]]
          },
          grid: {
            left: '3%',
            right: '4%',
            bottom: '10%',
            containLabel: true
          },

          tooltip: {
            show: "true",
            trigger: 'axis',
            axisPointer: { // 坐标轴指示器，坐标轴触发有效
              type: 'shadow' // 默认为直线，可选为：'line' | 'shadow'
            }
          },
          xAxis: {
            type: 'value',
            axisTick: {
              show: true
            },
            axisLine: {
              show: true,
              lineStyle: {
                color: '#fff',
              }
            },
            splitLine: {
              show: true
            },
          },
          yAxis: [{
            type: 'category',
            axisTick: {
              show: false
            },
            axisLine: {
              show: true,
              lineStyle: {
                color: '#fff',
              }
            },
            data: data.map(function (item) {
              return item.name;
            }),
          }

          ],
          series: [{
            name: this.drawingName[index],
            type: 'bar',
            itemStyle: {
              normal: {
                show: true,
                color: function(params) {
                  var num=myColor.length;
                  return myColor[params.dataIndex%num]
                },
                barBorderRadius: 50,
                borderWidth: 0,
                borderColor: '#333',
              }
            },
            barGap: '0%',
            barCategoryGap: '50%',
            data:  data.map(function (item) {
              return item.value;
            }),
          }]
        };
        drawChartId.setOption(option);
      },
      setoptinManyLin(drawChartId,title,singlePrice,totalPrice,area,dataTime){
        drawChartId.setOption({
        backgroundColor: '#394056',
        title: {
          text: title,
          textStyle: {
            fontWeight: 'normal',
            fontSize: 16,
            color: '#F1F1F3'
          },
          left: '6%'
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            animation: false,
            lineStyle: {
              color: '#57617B'
            }
          }
        },
        legend: {
          icon: 'rect',
          itemWidth: 14,
          itemHeight: 5,
          itemGap: 13,
          data: ['单价', '历史成交记录', '建筑面积'],
          right: '4%',
          textStyle: {
            fontSize: 12,
            color: '#F1F1F3'
          }
        },
          axisPointer: {
            link: {xAxisIndex: 'all'}
          },
        grid: [{
          // left: '3%',
          // right: '4%',
          // bottom: '3%',
          // containLabel: true
          left: 100,
          right: 100,
          height: '35%'
        },{
          // left: '3%',
          // right: '4%',
          // bottom: '3%',
          // top: '55.5%',
          // height: '35%',
          // containLabel: true
          left: 100,
          right: 100,
          top: '52.6%',
          height: '35%'
        }],
        xAxis: [{
          type: 'category',
          boundaryGap: false,
          axisLine: {
            lineStyle: {
              color: '#57617B'
            }
          },
          data: dataTime
        },{
          gridIndex: 1,
          type: 'category',
          boundaryGap: false,
          position: 'top',
          axisLine: {
            lineStyle: {
              color: '#57617B'
            }
          },
          data: dataTime
        },
          {
          // axisPointer: {
          //   show: false
          // },
          axisLine: {
            lineStyle: {
              color: '#57617B'
            }
          },
          // axisTick: {
          //   show: false
          // },
          position: 'bottom',
          offset: 20,
        }
        ],
        yAxis: [{
          type: 'value',
          name: '单位:(元/平方)',
          // axisTick: {
          //   show: false
          // },
          axisLine: {
            lineStyle: {
              color: '#57617B'
            }
          },
          // axisLabel: {
          //   margin: 10,
          //   textStyle: {
          //     fontSize: 14
          //   }
          // },
          splitLine: {
            lineStyle: {
              color: '#57617B'
            }
          }
        },{
          gridIndex: 1,
          type: 'value',
          inverse: true,
          name: '单位:(万元)(平方米)',
          // axisTick: {
          //   show: false
          // },
          axisLine: {
            lineStyle: {
              color: '#57617B'
            }
          },
          // axisLabel: {
          //   margin: 10,
          //   textStyle: {
          //     fontSize: 14
          //   }
          // },
          splitLine: {
            lineStyle: {
              color: '#57617B'
            }
          }
        }],
        series: [
          {
          name: '单价',
          type: 'line',
          smooth: true,
          symbol: 'circle',
          symbolSize: 5,
          showSymbol: false,
          lineStyle: {
            normal: {
              width: 1
            }
          },
          areaStyle: {
            normal: {
              color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                offset: 0,
                color: 'rgba(222, 0, 41, 0.3)'
              }, {
                offset: 0.8,
                color: 'rgba(222, 0, 41, 0)'
              }], false),
              shadowColor: 'rgba(0, 0, 0, 0.1)',
              shadowBlur: 10
            }
          },
          itemStyle: {
            normal: {
              color: 'rgb(222, 0, 41)',
              borderColor: 'rgba(222, 0, 41,0.27)',
              borderWidth: 12

            }
          },
          data: singlePrice
        },
          {
          name: '历史成交记录',
          type: 'line',
          smooth: true,
          xAxisIndex: 1,
          yAxisIndex: 1,
          symbol: 'circle',
          symbolSize: 5,
          showSymbol: false,
          lineStyle: {
            normal: {
              width: 1
            }
          },
          areaStyle: {
            normal: {
              color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                offset: 0,
                color: 'rgba(235, 135, 13, 0.3)'
              }, {
                offset: 0.8,
                color: 'rgba(235, 135, 13, 0)'
              }], false),
              shadowColor: 'rgba(0, 0, 0, 0.1)',
              shadowBlur: 10
            }
          },
          itemStyle: {
            normal: {
              color: 'rgb(235, 135, 13)',
              borderColor: 'rgba(235, 135, 13,0.2)',
              borderWidth: 12

            }
          },
          data: totalPrice
        }, {
          name: '建筑面积',
          type: 'line',
          smooth: true,
          xAxisIndex: 1,
          yAxisIndex: 1,
          symbol: 'circle',
          symbolSize: 5,
          showSymbol: false,
          lineStyle: {
            normal: {
              width: 1
            }
          },
          areaStyle: {
            normal: {
              color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                offset: 0,
                color: 'rgba(91,189,44, 0.3)'
              }, {
                offset: 0.8,
                color: 'rgba(91,189,44, 0)'
              }], false),
              shadowColor: 'rgba(0, 0, 0, 0.1)',
              shadowBlur: 10
            }
          },
          itemStyle: {
            normal: {

              color: 'rgb(91,189,44)',
              borderColor: 'rgba(91,189,44,0.2)',
              borderWidth: 12
            }
          },
          data: area
        }
          // {
          //   name: '一本',
          //   type: 'line',
          //   smooth: true,
          //   symbol: 'circle',
          //   symbolSize: 5,
          //   showSymbol: false,
          //   lineStyle: {
          //     normal: {
          //       width: 1
          //     }
          //   },
          //   areaStyle: {
          //     normal: {
          //       color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [{
          //         offset: 0,
          //         color: 'rgba(249, 245, 0, 0.3)'
          //       }, {
          //         offset: 0.8,
          //         color: 'rgba(249, 245, 0, 0)'
          //       }], false),
          //       shadowColor: 'rgba(0, 0, 0, 0.1)',
          //       shadowBlur: 10
          //     }
          //   },
          //   itemStyle: {
          //     normal: {
          //       color: 'rgb(249, 245, 0)',
          //       borderColor: 'rgba(249, 245, 0,0.27)',
          //       borderWidth: 12
          //
          //     }
          //   },
          //   data: this.dataNomal
          // },
          // {
          //   name: '二本',
          //   type: 'line',
          //   smooth: true,
          //   symbol: 'circle',
          //   symbolSize: 5,
          //   showSymbol: false,
          //   lineStyle: {
          //     normal: {
          //       width: 1
          //     }
          //   },
          //   areaStyle: {
          //     normal: {
          //       color: new this.$echarts.graphic.LinearGradient(0, 0, 0, 1, [{
          //         offset: 0,
          //         color: 'rgba(0,166, 174, 0.3)'
          //       }, {
          //         offset: 0.8,
          //         color: 'rgba(0,166, 174, 0)'
          //       }], false),
          //       shadowColor: 'rgba(0, 0, 0, 0.1)',
          //       shadowBlur: 10
          //     }
          //   },
          //   itemStyle: {
          //     normal: {
          //       color: 'rgb(0,166, 174)',
          //       borderColor: 'rgba(0,166, 174,0.27)',
          //       borderWidth: 12
          //
          //     }
          //   },
          //   data: this.dataLowNomal
          // }
          ]
      });

    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
