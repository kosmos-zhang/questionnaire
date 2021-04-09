<template>
  <div class="home" style="text-align:left; font-size: 1.5em">
    <h1>{{ msg }}</h1>
    <div>
      单位类型：
      <select name="unittype" v-model="unittype" >
        <option v-for="(item, index) in unitlst" :key="index" :value="item" >{{item.name}}</option>
      </select>
    </div>
    <div>
      单位名称：
      <select name="unitgroup" v-model="unitgroup" >
        <option v-for="(item, index) in unittype.groups" :key="index" :value="item" >{{item.name}}</option>
      </select>
      <select name="unit" v-model="unit" >
        <option v-for="(item, index) in unitgroup.units" :key="index" :value="item" >{{item.name}}</option>
      </select>
    </div>
    <div>
      <ul>
        <li>
          1. 该单位所有建筑物入口是否由清晰明显的禁止吸烟提示
          <input type="radio">是
          <input type="radio">否
        </li>
        <li>
          2. 室内场所类型：
          <select>
            <option>食堂</option>
            <option>一楼大厅</option>
            <option>电梯</option>
            <option>会议室</option>
            <option>办公室</option>
            <option>男厕所</option>
            <option>走廊</option>
            <option>楼梯</option>
            <option>传达室(门卫)</option>
            <option>其他</option>
          </select>
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
export default {
  name: 'Home',
  data () {
    return {
      msg: '控烟状况记录表',
      unittype: '',
      unitgroup: '',
      unit: '',
      unitlst: [{
        'type': 1,
        'name': '机关',
        'groups': [{
          'type': 1,
          'name': '一组',
          'units': [
            {'id': '1-01', 'name': '大团镇'},
            {'id': '1-02', 'name': '区农业农村委'},
            {'id': '1-03', 'name': '南汇新城镇'},
            {'id': '1-04', 'name': '临港新片区管委会'},
            {'id': '1-05', 'name': '书院镇'},
            {'id': '1-06', 'name': '泥城镇'},
            {'id': '1-07', 'name': '万祥镇'},
            {'id': '1-08', 'name': '老港镇'}
          ]
        }, {
          'type': 2,
          'name': '二组',
          'units': [
            {'id': '2-01', 'name': '惠南镇'},
            {'id': '2-02', 'name': '祝桥镇'},
            {'id': '2-03', 'name': '宣桥镇'},
            {'id': '2-04', 'name': '新场镇'},
            {'id': '2-05', 'name': '航头镇'}
          ]
        }, {
          'type': 3,
          'name': '三组',
          'units': [
            {'id': '3-01', 'name': '度假区管委会'},
            {'id': '3-02', 'name': '川沙新镇'},
            {'id': '3-03', 'name': '张江镇'},
            {'id': '3-04', 'name': '自贸区张江管理局'},
            {'id': '3-05', 'name': '周浦镇'},
            {'id': '3-06', 'name': '康桥镇'},
            {'id': '3-07', 'name': '区城管执法局'},
            {'id': '3-08', 'name': '三林镇'},
            {'id': '3-09', 'name': '北蔡镇'},
            {'id': '3-10', 'name': '区残联'},
            {'id': '3-11', 'name': '区卫生健康委'},
            {'id': '3-12', 'name': '区民政局'},
            {'id': '3-13', 'name': '区司法局'},
            {'id': '3-14', 'name': '区生态环境局'},
            {'id': '3-15', 'name': '区卫生健康委'},
            {'id': '3-16', 'name': '区审计局'},
            {'id': '3-17', 'name': '区科协'}
          ]
        }, {
          'type': 4,
          'name': '四组',
          'units': [
            {'id': '4-01', 'name': '曹路镇'},
            {'id': '4-02', 'name': '合庆镇'},
            {'id': '4-03', 'name': '金桥镇'},
            {'id': '4-04', 'name': '自贸区金桥管理局'},
            {'id': '4-05', 'name': '唐镇'},
            {'id': '4-06', 'name': '自贸区保税区管理局'},
            {'id': '4-07', 'name': '高桥镇'},
            {'id': '4-08', 'name': '高行镇'},
            {'id': '4-09', 'name': '高东镇'}
          ]
        }, {
          'type': 5,
          'name': '五组',
          'units': [
            {'id': '5-01', 'name': '上钢新村街道'},
            {'id': '5-02', 'name': '周家渡街道'},
            {'id': '5-03', 'name': '潍坊新村街道'},
            {'id': '5-04', 'name': '区税务局'},
            {'id': '5-05', 'name': '南码头路街道'},
            {'id': '5-06', 'name': '塘桥街道'},
            {'id': '5-07', 'name': '区金融局'},
            {'id': '5-08', 'name': '东明路街道'}
          ]
        }, {
          'type': 6,
          'name': '六组',
          'units': [
            {'id': '6-01', 'name': '沪东新村街道'},
            {'id': '6-02', 'name': '区人民武装部'},
            {'id': '6-03', 'name': '区应急局'},
            {'id': '6-04', 'name': '洋泾街道'},
            {'id': '6-05', 'name': '自贸区世博管理局'},
            {'id': '6-06', 'name': '区市场监管局'},
            {'id': '6-07', 'name': '区工商联'},
            {'id': '6-08', 'name': '区侨联'},
            {'id': '6-09', 'name': '区委政法委'},
            {'id': '6-10', 'name': '区信访办'},
            {'id': '6-11', 'name': '区公安分局'},
            {'id': '6-12', 'name': '区法院'},
            {'id': '6-13', 'name': '区检察院'},
            {'id': '6-14', 'name': '区档案局'},
            {'id': '6-15', 'name': '国家统计局浦东调查队'},
            {'id': '6-16', 'name': '区知识产权局'},
            {'id': '6-17', 'name': '区红十字会'},
            {'id': '6-18', 'name': '陆家嘴街道'},
            {'id': '6-19', 'name': '自贸区陆家嘴管理局'},
            {'id': '6-20', 'name': '区总工会'},
            {'id': '6-21', 'name': '花木街道'},
            {'id': '6-22', 'name': '区教育局'},
            {'id': '6-23', 'name': '区规划资源局'},
            {'id': '6-24', 'name': '区国资委'},
            {'id': '6-25', 'name': '团区委'},
            {'id': '6-26', 'name': '区妇联'},
            {'id': '6-27', 'name': '浦兴路街道'}
          ]
        }, {
          'type': 7,
          'name': '七组',
          'units': [
            {'id': '7-01', 'name': '区纪委'},
            {'id': '7-02', 'name': '区委办公室'},
            {'id': '7-03', 'name': '区委组织部'},
            {'id': '7-04', 'name': '区委宣传部'},
            {'id': '7-05', 'name': '区委统战部'},
            {'id': '7-06', 'name': '区地区工作党委'},
            {'id': '7-07', 'name': '区级机关工作党委'},
            {'id': '7-08', 'name': '区人大常委会办公室'},
            {'id': '7-09', 'name': '区政府办公室'},
            {'id': '7-10', 'name': '区科经委'},
            {'id': '7-11', 'name': '区商务委'},
            {'id': '7-12', 'name': '区财政局'},
            {'id': '7-13', 'name': '区人社局'},
            {'id': '7-14', 'name': '区建交委'},
            {'id': '7-15', 'name': '区政协办公室'},
            {'id': '7-16', 'name': '区发改委'}
          ]
        }]
      }, {
        'type': 2,
        'name': '医疗卫生单位',
        'groups': [{
          'type': 1,
          'name': '社区卫生服务中心（一）',
          'units': [
            {'id': '1-01', 'name': '大团社区卫生服务中心'},
            {'id': '1-02', 'name': '芦潮港社区卫生服务中心'},
            {'id': '1-03', 'name': '书院社区卫生服务中心'},
            {'id': '1-04', 'name': '泥城社区卫生服务中心'},
            {'id': '1-05', 'name': '万祥社区卫生服务中心'},
            {'id': '1-06', 'name': '老港社区卫生服务中心'},
            {'id': '1-07', 'name': '惠南社区卫生服务中心'},
            {'id': '1-08', 'name': '机场镇社区卫生服务中心'},
            {'id': '1-09', 'name': '祝桥社区卫生服务中心'},
            {'id': '1-10', 'name': '江镇社区卫生服务中心'},
            {'id': '1-11', 'name': '宣桥社区卫生服务中心'},
            {'id': '1-12', 'name': '新场社区卫生服务中心'},
            {'id': '1-13', 'name': '航头社区卫生服务中心'}
          ]
        }, {
          'type': 2,
          'name': '社区卫生服务中心（二）',
          'units': [
            {'id': '2-01', 'name': '川沙社区卫生服务中心'},
            {'id': '2-02', 'name': '黄楼社区卫生服务中心'},
            {'id': '2-03', 'name': '六团社区卫生服务中心'},
            {'id': '2-04', 'name': '孙桥社区卫生服务中心'},
            {'id': '2-05', 'name': '六灶社区卫生服务中心'},
            {'id': '2-06', 'name': '张江社区卫生服务中心'},
            {'id': '2-07', 'name': '周浦社区卫生服务中心'},
            {'id': '2-08', 'name': '康桥社区卫生服务中心'},
            {'id': '2-09', 'name': '三林社区卫生服务中心'},
            {'id': '2-10', 'name': '北蔡社区卫生服务中心'},
            {'id': '2-11', 'name': '迎博社区卫生服务中心'}
          ]
        }, {
          'type': 3,
          'name': '社区卫生服务中心（三）',
          'units': [
            {'id': '3-01', 'name': '曹路社区卫生服务中心'},
            {'id': '3-02', 'name': '合庆社区卫生服务中心'},
            {'id': '3-03', 'name': '金桥社区卫生服务中心'},
            {'id': '3-04', 'name': '王港社区卫生服务中心'},
            {'id': '3-05', 'name': '唐镇社区卫生服务中心'},
            {'id': '3-06', 'name': '高桥社区卫生服务中心'},
            {'id': '3-07', 'name': '凌桥社区卫生服务中心'},
            {'id': '3-08', 'name': '高行社区卫生服务中心'},
            {'id': '3-09', 'name': '高东社区卫生服务中心'}
          ]
        }, {
          'type': 4,
          'name': '社区卫生服务中心（四）',
          'units': [
            {'id': '4-01', 'name': '上钢社区卫生服务中心'},
            {'id': '4-02', 'name': '周家渡社区卫生服务中心'},
            {'id': '4-03', 'name': '潍坊社区卫生服务中心'},
            {'id': '4-04', 'name': '南码头社区卫生服务中心'},
            {'id': '4-05', 'name': '塘桥社区卫生服务中心'},
            {'id': '4-06', 'name': '东明社区卫生服务中心'},
            {'id': '4-07', 'name': '沪东社区卫生服务中心'},
            {'id': '4-08', 'name': '洋泾社区卫生服务中心'},
            {'id': '4-09', 'name': '金杨社区卫生服务中心'},
            {'id': '4-10', 'name': '陆家嘴社区卫生服务中心'},
            {'id': '4-11', 'name': '联洋社区卫生服务中心'},
            {'id': '4-12', 'name': '花木社区卫生服务中心'},
            {'id': '4-13', 'name': '浦兴社区卫生服务中心'}
          ]
        }, {
          'type': 5,
          'name': '市级医院',
          'units': [
            {'id': '5-01', 'name': '儿童医学中心'},
            {'id': '5-02', 'name': '市一妇婴（北蔡）'},
            {'id': '5-03', 'name': '市六医院东院'},
            {'id': '5-04', 'name': '曙光医院东院'},
            {'id': '5-05', 'name': '一妇婴浦东分院'},
            {'id': '5-06', 'name': '仁济医院'},
            {'id': '5-07', 'name': '龙华东院'},
            {'id': '5-08', 'name': '华山医院东院'},
            {'id': '5-09', 'name': '市九医院浦东分院'}
          ]
        }, {
          'type': 6,
          'name': '二级以上医院',
          'units': [
            {'id': '6-01', 'name': '东方医院'},
            {'id': '6-02', 'name': '东方医院南院'},
            {'id': '6-03', 'name': '人民医院'},
            {'id': '6-04', 'name': '浦东医院'},
            {'id': '6-05', 'name': '第七人民医院'},
            {'id': '6-06', 'name': '公利医院'},
            {'id': '6-07', 'name': '浦南医院'},
            {'id': '6-08', 'name': '周浦医院'},
            {'id': '6-09', 'name': '中医医院'},
            {'id': '6-10', 'name': '光明中医医院'},
            {'id': '6-11', 'name': '妇幼保健院'},
            {'id': '6-12', 'name': '浦东新区精神卫生中心'},
            {'id': '6-13', 'name': '南汇精神卫生中心'},
            {'id': '6-14', 'name': '肺科医院'},
            {'id': '6-15', 'name': '传染病医院'},
            {'id': '6-16', 'name': '南华医院'},
            {'id': '6-17', 'name': '老年医院'}
          ]
        }, {
          'type': 7,
          'name': '直属单位',
          'units': [
            {'id': '7-01', 'name': '医疗机构管理中心'},
            {'id': '7-02', 'name': '卫生发展研究院'},
            {'id': '7-03', 'name': '卫生资源管理中心'},
            {'id': '7-04', 'name': '医疗事故鉴定中心'},
            {'id': '7-05', 'name': '疾病预防控制中心'},
            {'id': '7-06', 'name': '卫生监督所'},
            {'id': '7-07', 'name': '爱卫办'},
            {'id': '7-08', 'name': '人口和计划生育管理中心'},
            {'id': '7-09', 'name': '医疗急救中心'},
            {'id': '7-10', 'name': '血液管理办公室'},
            {'id': '7-11', 'name': '卫生学校'},
            {'id': '7-12', 'name': '妇幼保健所'},
            {'id': '7-13', 'name': '眼牙防所'}
          ]
        }, {
          'type': 8,
          'name': '其他',
          'units': [
            {'id': '8-01', 'name': '长航医院'},
            {'id': '8-02', 'name': '沪东职工医院'}
          ]
        }]
      }]
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
</style>
