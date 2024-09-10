<template>
  <div>
    <h2>模板语法</h2>
    <p>{{ message }} </p>
    <p>{{ message.split("").reverse().join("") }}</p>
    <p>{{ code + 1 }} </p>
    <p>{{ ok ? "YES" : "NO" }}</p>

    <p>{{ htmlTemp }}</p>
    <p v-html="htmlTemp"></p>

  </div>

  <div>
    <h2>属性绑定</h2>
    <p v-bind:id="id" v-bind:class="class1">测试</p>
    <button v-bind:disabled="disabled">按钮</button>

    <p v-bind="obj">测试</p>
  </div>

  <div>
    <h2>条件渲染</h2>

    <!-- 渲染满足条件的元素 -->
    <p v-if="isOk">YES</p>
    <p v-else>NO</p>

    <p v-if="tag == 'A'">A</p>
    <p v-else-if="tag == 'B'">B</p>
    <p v-else-if="tag == 'C'">C</p>
    <!-- 一直渲染，通过display: none 控制显示&不显示 -->
    <p v-show="isOk">显示</p>
  </div>

  <div>
    <h2>列表渲染</h2>
    <p v-for="name, index in names" :key="index">{{ name }}</p>
    <p v-for="(name, index) in names" :key="index">{{ name }}</p>

    <div v-for="emp of employees" :key="emp.id">
      <p>id:{{ emp.id }}</p>
      <p>name:{{ emp.name }}</p>
    </div>
    <!-- 遍历对象 -->
    <div v-for="(value, key, index) of userInfo" :key="key">
      <p>{{ index }}:{{ key }}:{{ value }}</p>
    </div>
  </div>


  <div>
    <h2>事件处理</h2>
    <p>{{ count }}</p>
    <button v-on:click="count++">按钮</button>
    <button @:click="count++">按钮</button>
    <p>{{ count }}</p>
    <button @click="addCount($event)">按钮</button>

    <!-- 事件传参 -->
    <p @click="getName(name, $event)" v-for="(name, index) in names" :key="index">{{ name }}</p>

    <!-- 事件修饰符 -->
    <a @click="baidu" href="http://www.baidu.com">百度一下</a>
    <!-- 使用修饰符 -->
    <a @click.prevent="baidu" href="http://www.baidu.com">百度一下</a>

    <div @click="clickDiv">
      <p @click.stop="clickP">测试冒泡</p>
    </div>

  </div>

  <div>
    <h2>数组变化侦听</h2>
    <button @click="addName">添加数据</button>
    <ul>
      <li v-for="(name, index) of names" :key="index">{{ name }}</li>
    </ul>

  </div>

  <div>
    <h2>class绑定</h2>
    <p :class="{ active: active, class1: class1 }">测试</p>
    <p :class="classObj">测试1</p>

    <p :class="[active, class1]">测试2</p>
    <p :class="classArr">测试3</p>

  </div>

  <div>
    <h2>style绑定</h2>
    <p :style="{ color: 'red', fontSize: '20px', fontWeight: 'bold' }">测试</p>
    <p :style="{ color: color, fontSize: fontSize, fontWeight: fontWeight }">测试1</p>
    <p :style="styleObj">测试2</p>
    <p :style="[styleObj]">测试3</p>
  </div>

  <div>
    <h2>侦听器</h2>
    <p>{{ message }}</p>
    <input type="text" v-model="message">
  </div>

  <div>
    <h2>表单输入与绑定</h2>

    <p>输入文本:{{ msg }}</p>
    <input type="text" id="msg" v-model="msg">

    <p>输入文本:{{ msg }}</p>
    <textarea type="text" id="msg" v-model="msg"></textarea>

    <p>已选择：{{ checked }}</p>
    <input type="checkbox" id="A" value="A" v-model="checked">
    <label  for="A">A</label >
    <input type="checkbox" id="B" value="B" v-model="checked">
    <label  for="B">B</label >

    <p>已选择：{{ picked }}</p>
    <input type="radio" id="男" value="男" v-model="picked">
    <label  for="男">男</label >
    <input type="radio" id="女" value="女" v-model="picked">
    <label  for="女">女</label >

    <p>已选择：{{ selected }}</p>
    <select name="selected" id="selected" multiple v-model="selected">
      <option value="" disabled>请选择</option>
      <option value="A">A</option>
      <option value="B">B</option>
      <option value="C">C</option>
    </select>
  </div>

  <div>
    <h2>模板引用（操作DOM）</h2>
    <div ref="message">{{ message }}</div>
    <input type="text" ref="username" value="" >

    <button @click="changeMessage">修改</button>
  </div>

  <div>
    <h2>动态组件</h2>
    <component1/>
    <component1></component1>
  </div>

  <div>
    <h2>组件传递数据</h2>
    <componentA/>
  </div>

  <div>
    <h2>组件事件（子组件给父组件传递数据）</h2>
    <componentB/>
  </div>


 <div>
    <h2>透传属性</h2>
    <!-- 子组件必须是唯一根节点 -->
    <attrComponent id="111" class="attr"/>
  </div>

  <div>
    <h2>插槽</h2>
    <slotComponent >
      
      <!-- <span style="color: red;">插槽内容</span>  
      <p>{{ slotContent }} </p> -->
      
    </slotComponent>


    <slotComponent>

     <!-- 具名插槽1 -->
      <template v-slot:slot1>
        <p>具名插槽1内容 </p>
      </template>

      <!-- 具名插槽2 -->
      <template #slot2>
        <p>具名插槽2内容111</p>
      </template>


      <!-- 作用域插槽 -->
      <template v-slot="slotProps">
        <p>{{ slotContent }} -- {{ slotProps.msg }}</p>
      </template>

      <!-- 具名作用域插槽  -->
      <template v-slot:slot3="slotProps">
        <p>{{ slotContent }} -- {{ slotProps.msg }}</p>
      </template>
      

    </slotComponent>

  </div>

</template>


<script>

// 引入组件
import component1 from "./components/component1.vue";
import componentA from './components/componentA.vue';
import componentB from './components/componentB.vue';
import attrComponent from './components/attrComponent.vue';
import slotComponent from "./components/slotComponent.vue";


export default {

  // 注册组件
  components:{
    component1,
    componentA,
    componentB,
    attrComponent,
    slotComponent
  },


  data() {
    return {
      //模板语法
      message: "测试",
      code: 110,
      ok: true,
      htmlTemp: "<a href='https://www.baidu.com'>百度一下</a></h2>",

      // 属性绑定
      id: 10001,
      name: "test",
      class1: "class1",
      disabled: false,
      obj: {
        id: 10001,
        name: "test",
      },

      //条件渲染
      isOk: false,
      tag: "C",

      //列表渲染
      names: ["张三", "李四", "王五"],
      employees: [
        { id: 10001, name: "张三" },
        { id: 10002, name: "李四" },
        { id: 10003, name: "王五" }
      ],
      userInfo: {
        id: 10001,
        username: "张三",
        password: "123456"
      },

      //事件处理
      count: 0,

      //class绑定
      active: 'active',

      classObj: {
        active: true,
        class1: true,
        // active:'active',
        // class1:'class1',
      },
      classArr: ['active', 'class1'],

      //style绑定
      color: 'red',
      fontSize: '20px',
      fontWeight: 'bold',
      styleObj: {
        color: 'red',
        fontSize: '20px',
        fontWeight: 'bold'
      },
      //表单输入绑定
      msg: null,
      checked: [],
      picked: '',
      selected: [],

      //插槽
      slotContent:"插槽内容"

    }
  },

  watch: {
    //侦听器
    message: {
      handler(newValue, oldValue) {
        console.log(newValue);
        console.log(oldValue);
      },
      immediate: true
    }
  },

  methods: {
  
    changeMessage() {
      this.$refs.message.innerHTML = "修改后";

      console.log(this.$refs.username.value);

    },

    addCount(e) {
      e.target.innerHTML = "Add:" + this.count;
      this.count++;
    },

    getName(name, e) {
      console.log(name);
      console.log(e.target);
    },

    baidu(e) {
      //阻止默认事件（跳转百度）
      // e.preventDefault();
      console.log("百度一下");
    },

    clickDiv() {
      console.log("div");
    },

    clickP() {
      console.log("p");
    },

    addName() {
      //原数组会变, ui更新 push() pop() shift() unshift() splice() sort() reverse()
      // this.names.push("测试数据");

      //原数组不会变, ui不更新 filter() concat() slice()
      this.names.concat(["测试数据"]);
      console.log(this.names);
    },
  }
}

</script>



<style>
.active {
  color: green;
}


.class1 {
  font-size: 20px;
  font-weight: bold;
}
</style>
