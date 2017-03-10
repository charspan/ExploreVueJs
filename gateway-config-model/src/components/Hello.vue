<template>
  <div class="hello">
    <form name="form" method="POST" action="">
        <div class="objcode">
            <ul style="text-align: left;">
                <p>EIB/KNX 实现逻辑/场景功能</p>
                <li>
                    <div class="ul_1">对象名称：</div>
                </li>
                <li>
                    <div class="ul_2">
                        <input type="text" name="oName" v-model="oName"> 
                    </div>
                </li>
                <li>
                    <div class="ul_1">接受EIS 类型：</div>
                </li>
                <li>
                    <div class="ul_2">
                        <select name="EIS" v-model='arg2_selected' class="EIS">
                            <option v-for='arg2 in arg2_options' v-bind:value='arg2.value'>
                                {{arg2.text}}
                            </option>
                        </select>
                    </div>
                </li>
                <li>
                    <div class="ul_1">接受KNX 组地址：</div>
                </li>
                <li>
                    <div class="ul_2">
                        <input type="text" name="gad_status" v-model="gad_status">
                    </div>
                </li>
                <li>
                    <div class="ul_1">接受时间条件：</div>
                </li>
                <li>
                    <div class="ul_2">
                        <input type="text" name="oButONICON" v-model="oButONICON"> [例如 00:00~09:30]</div>
                </li>
                <li>
                    <div class="ul_1">接受值匹配：</div>
                </li>
                <li>
                    <div class="ul_2">
                        <select name="widthX" v-model="widthX_selected"style="width:65px;">
                            <option v-for='widthX in widthX_options' v-bind:value='widthX.value'>
                                    {{widthX.text}}
                            </option>
                        </select>
                        <input type="text" name="gad_value" style="width:120px;" v-model="gad_value"> [-1=接受任意数值] </div>
                </li>
                <li>
                    <div class="ul_1">[Tx All] 触发延迟[s]</div>
                </li>
                <li>
                    <div class="ul_2">
                        <input type="text" name="positionX" v-model="positionX">
                    </div>
                </li>
                <li>
                    <div class="ul_1">[Tx All] 触发EIS类型</div>
                </li>
                <li>
                    <div class="ul_2">
                        <select name="arg2" v-model='arg2_selected' class="EIS">
                            <option v-for='arg2 in arg2_options' v-bind:value='arg2.value'>
                                {{arg2.text}}
                            </option>
                        </select>
                    </div>
                </li>
                <li>
                    <div class="ul_1">[Tx All] 触发值匹配</div>
                </li>
                <li>
                    <div class="ul_2">
                        <select name="heightY" v-model='heightY_selected' style="width:65px;">
                            <option v-for='heightY in heightY_options' v-bind:value='heightY.value'>
                                {{heightY.text}}
                            </option>
                        </select>
                        <span style="display:none;">获取值:{{ heightY_selected }}</span>
                        <input type="text" name="arg3" style="width:120px;" v-model="arg3"> [-1=触发接受的数值]</div>
                </li>
                <li>
                    <div>
                        <img src="../assets/tips.png" alt="">
                        <textarea name="arg1" cols="80" rows="3" v-model="arg1"></textarea>
                    </div>
                </li>
            </ul>
        </div>
    </form>
</div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      oName: '模式-冷',
      gad_status: '15/0/2',
      positionX: 0,
      gad_value: 2,
      oButONICON: '',
      arg3: 3,
      arg1: '13/0/2',
      widthX_selected: '0',
      widthX_options: [
        { text: '等于', value: '0' },
        { text: '不等于', value: '1' },
        { text: '大于', value: '2' },
        { text: '小于', value: '3' }
      ],
      arg2_selected: '4',
      arg2_options: [
        { text: '请选择EIB/KNX数据类型', value: '0' },
        { text: 'READ: KNX Read', value: '0' },
        { text: 'EIS1: EIB_switch(1bit)', value: '1' },
        { text: 'EIS2: EIB_dimming_control(4bits)', value: '2' },
        { text: 'EIS5: EIB_Float_value (2Byte)', value: '3' },
        { text: 'EIS6: EIB_value (1Byte)', value: '4' },
        { text: 'EIS7: EIB_drive (1bit)', value: '5' },
        { text: 'EIS8: EIB_Priority_control(2bits)', value: '6' },
        { text: 'EIS10: EIB_Count_Value (2Byte)', value: '7' },
        { text: 'EIS11: EIB_Count_Value (4Byte)', value: '8' },
        { text: 'EIS13: EIB_ASCII_Character(8bits)', value: '9' }
      ],
      heightY_selected: '=',
      heightY_options: [
        { text: '等于', value: '=' },
        { text: '加', value: '+' },
        { text: '减', value: '-' },
        { text: '乘', value: '*' },
        { text: '除', value: '/' }
      ]
    }
  }
}
</script>

<script type="text/javascript"></script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import '/static/css/form.css';

label{float: left;width: 80px;line-height:25px;} 
form{margin:0px} 
input{width: 180px;border:1px solid #808080;} 
textarea{width: 250px;height: 150px;} 
 
#sbutton{margin-left: 80px;margin-top: 5px;width:80px;} 
 
br{clear: left;} 

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
