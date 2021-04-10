<template>
  <div class="home">
    <h1 style="text-align:center;">{{ msg }}</h1>
    <el-row>
      <el-col class="rowCls" :span="8"><span>单位类型：</span></el-col>
      <el-col :span="12">
        <el-select name="unittype" v-model="unittype" value-key="type" @change="unitTypeSelect" >
          <el-option v-for="item in unitlst" :key="item.type" :value="item" :label="item.name"></el-option>
        </el-select>
      </el-col>
    </el-row>
    <el-row>
      <el-col class="rowCls" :span="8">单位名称：</el-col>
      <el-col :span="12">
        <el-select name="unitgroup" v-model="unitgroup" value-key="type" >
          <el-option v-for="item in unittype.groups" :key="item.type" :value="item" :label="item.name"></el-option>
        </el-select>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="8">&nbsp;</el-col>
      <el-col :span="12">
        <el-select name="unit" v-model="unit" value-key="id" >
          <el-option v-for="item in unitgroup.units" :key="item.id" :value="item" :label="item.name"></el-option>
        </el-select>
      </el-col>
    </el-row>
    <div style="background-color: #cdcdcd; height:1px; width:100%; margin:20px 0 0 0"> </div>
    <ul>
      <li class="questItem">
        <el-row class="quest">
          <span>1. 该单位所有建筑物入口是否由清晰明显的禁止吸烟提示</span>
        </el-row>
        <el-row class="answer">
          <el-radio-group v-model="form.isChecked1">
            <el-radio :label="1">是</el-radio>
            <el-radio :label="0">否</el-radio>
          </el-radio-group>
        </el-row>
        <el-row class="remark">
          <el-col :span="22">
            <textarea :disabled="form.isChecked1==0" style="height: 50px; width:100%;" />
          </el-col>
        </el-row>
      </li>
      <el-row>
        <ul>
          <li>
            2. 室内场所类型：
            <!--<el-select>
              <el-option>食堂</el-option>
              <el-option>一楼大厅</el-option>
              <el-option>电梯</el-option>
              <el-option>会议室</el-option>
              <el-option>办公室</el-option>
              <el-option>男厕所</el-option>
              <el-option>走廊</el-option>
              <el-option>楼梯</el-option>
              <el-option>传达室(门卫)</el-option>
              <el-option>其他</el-option>
            </el-select>-->
            <ul>
              <li>
                (1) 是否有规范的禁烟标识
                <input type="radio">是
                <input type="radio">否
              </li>
              <li>
                (2) 是否有烟味
                <input type="radio">是
                <input type="radio">否
              </li>
              <li>
                (3) 是否有人吸烟
                <input type="radio">是
                <input type="radio">否
              </li>
              <li>
                (4) 是否有烟具(如烟灰缸等)
                <input type="radio">是
                <input type="radio">否
              </li>
              <li>
                (5) 是否有烟头
                <input type="radio">是
                <input type="radio">否
              </li>
            </ul>
          </li>
        </ul>
      </el-row>
      <li class="questItem">
        <el-row class="quest">
          3. 该单位是否设置室外吸烟区
        </el-row>
        <el-row class="answer">
          <el-radio-group v-model="form.isChecked3">
            <el-radio :label="1">是</el-radio>
            <el-radio :label="0">否</el-radio>
          </el-radio-group>
        </el-row>
        <el-row class="remark">
          <el-checkbox-group v-model="form.checkList3" :disabled="form.isChecked3==0">
            <el-checkbox class="answer" label="a">a. 是否远离密集人群和必经通道</el-checkbox>
            <el-checkbox class="answer" label="b">b. 是否有明显的引导标识</el-checkbox>
            <el-checkbox class="answer" label="c">c. 是否有温馨提示</el-checkbox>
          </el-checkbox-group>
        </el-row>
      </li>
      <li class="questItem">
        <el-row class="quest">
          4. 该单位是否有创建无烟党政机关的承诺在显著位置张贴或摆放
        </el-row>
        <el-row class="answer">
          <el-radio-group v-model="form.isChecked4">
            <el-radio :label="1">是</el-radio>
            <el-radio :label="0">否</el-radio>
          </el-radio-group>
        </el-row>
      </li>
      <li class="questItem">
        <el-row class="quest">
          5. 该单位是否有一定数量和种类的控烟宣传形式，如新媒体，电视，展板，宣传栏，海报，折页，标语等
        </el-row>
        <el-row class="answer">
          <el-radio-group v-model="form.isChecked5">
            <el-radio :label="3">3种及以上</el-radio>
            <el-radio :label="2">2种</el-radio>
            <el-radio :label="1">1种</el-radio>
            <el-radio :label="0">无</el-radio>
          </el-radio-group>
        </el-row>
      </li>
      <li class="questItem">
        <el-row class="quest">
          6. 该单位内商店，小卖部，食堂等是否出售烟草制品
        </el-row>
        <el-row class="answer">
          <el-radio-group v-model="form.isChecked6">
            <el-radio :label="1">是</el-radio>
            <el-radio :label="0">否</el-radio>
          </el-radio-group>
        </el-row>
        <el-row class="remark">
          <textarea :disabled="form.isChecked6==0" style="height: 50px; width:100%;" />
        </el-row>
      </li>
      <li class="questItem">
        <el-row class="quest">
          7. 该单位是否有烟草广告，促销或赞助
        </el-row>
        <el-row class="answer">
          <el-radio-group v-model="form.isChecked7">
            <el-radio :label="1">是</el-radio>
            <el-radio :label="0">否</el-radio>
          </el-radio-group>
        </el-row>
        <el-row class="remark">
          <el-col :span="24">
            <textarea :disabled="form.isChecked7==0" style="height: 50px; width:100%;" />
          </el-col>
        </el-row>
      </li>
      <el-row>
        最终得分：{{form.total}}
      </el-row>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Home',
  data () {
    return {
      msg: '控烟状况记录表',
      unittype: '',
      unitgroup: '',
      unit: '',
      unitlst: [],
      form: {
        isChecked1: 1,
        isChecked3: 1,
        checkList3: [],
        isChecked4: 1,
        isChecked5: 1,
        isChecked6: 0,
        isChecked7: 0,
        total: 0
      }
    }
  },
  mounted () {
    this.loadUnits()
  },
  methods: {
    loadUnits () {
      var _that = this
      axios.get('/static/mock/unit.json').then((res) => {
        _that.unitlst = res.data
        _that.resetDefault(0)
      })
    },
    resetDefault (type) {
      if (type === 0) {
        this.unittype = this.unitlst[0]
      }
      if (type <= 1) {
        this.unitgroup = this.unittype.groups[0]
      }
      if (type <= 2) {
        this.unit = this.unitgroup.units[0]
      }
    },
    unitTypeSelect (val) {
      this.resetDefault(1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 8px 2px;
}
a {
  color: #42b983;
}
.home {
  font-size: 1.4em;
  text-align: left;
}
.el-select /deep/ .el-input__inner {
  font-size:20px !important;
}
.el-select-dropdown__item  {
  font-size:20px !important;
}
.el-radio /deep/ .el-radio__label{
  font-size:20px !important;
}
.el-checkbox /deep/ .el-checkbox__label {
  font-size:20px !important;
}
.rowCls {
  height: 40px;
  line-height: 40px;
}
.questItem {
  margin-top: 15px;
}
.questItem .quest {
  font-weight: bolder;
}
.questItem .answer {
  margin: 5px 0 0 20px;
}
.questItem .remark {
  margin: 5px 0 0 15px;
}
</style>
