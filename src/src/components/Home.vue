<template>
  <div class="home">
    <h1 style="text-align:center;">{{ msg }}</h1>
    <el-row class="rowCls">
      <el-col :span="6"><span>单位类型：</span></el-col>
      <el-col :span="9">
        <el-select name="unittype" v-model="unittype" value-key="type" @change="unitTypeSelect" >
          <el-option v-for="item in unitlst" :key="item.type" :value="item" :label="item.name"></el-option>
        </el-select>
      </el-col>
    </el-row>
    <el-row class="rowCls">
      <el-col :span="6">单位名称：</el-col>
      <el-col :span="9">
        <el-select name="unitgroup" v-model="unitgroup" value-key="type" >
          <el-option v-for="item in unittype.groups" :key="item.type" :value="item" :label="item.name"></el-option>
        </el-select>
      </el-col>
      <el-col :span="9">
        <el-select name="unit" v-model="unit" value-key="id" >
          <el-option v-for="item in unitgroup.units" :key="item.id" :value="item" :label="item.name"></el-option>
        </el-select>
      </el-col>
    </el-row>
    <el-row class="rowCls">
      <el-row>
        <span>1. 该单位所有建筑物入口是否由清晰明显的禁止吸烟提示</span>
      </el-row>
      <el-row>
      </el-row>
    </el-row>
    <div>
      <ul>
        <li>
          1. 该单位所有建筑物入口是否由清晰明显的禁止吸烟提示
          <input type="radio">是
          <input type="radio">否
        </li>
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
        <li>
          3. 该单位是否设置室外吸烟区
          <input type="radio">是
          <input type="radio">否
        </li>
        <li>
          4. 该单位是否有创建无烟党政机关的承诺在显著位置张贴或摆放
          <input type="radio">是
          <input type="radio">否
        </li>
        <li>
          5. 该单位是否有一定数量和种类的控烟宣传形式，如新媒体，电视，展板，宣传栏，海报，折页，标语等
          <input type="radio">是
          <input type="radio">否
        </li>
        <li>
          6. 该单位内商店，小卖部，食堂等是否出售烟草制品
          <input type="radio">是
          <input type="radio">否
        </li>
        <li>
          7. 该单位是否有烟草广告，促销或赞助
          <input type="radio">是
          <input type="radio">否
        </li>
      </ul>
      <div>
        最终得分：
      </div>
    </div>
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
      unitlst: []
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
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.home {
  font-size: 1em;
  text-align: left;
}
.rowCls {
  height: 40px;
  line-height: 40px;
}
</style>
