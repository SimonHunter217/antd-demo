<template>
  <a-layout class="home-layout">
    <a-layout-header class="home-layout-header">
      <div class="title-text">Antd-demo</div>
    </a-layout-header>
    
    <a-layout class="content-layout">
      <a-layout-sider collapsible>
        <a-menu
          :defaultSelectedKeys="['1']"
          mode="inline"
          theme="dark"
        >
          <a-menu-item key="1">
            <a-icon type="file"></a-icon>
            <span>基础</span>
          </a-menu-item>
          <a-menu-item key="2">进阶</a-menu-item>
        </a-menu>
      </a-layout-sider>
      
      <a-layout>
        <a-layout-content>
          <div>
            <a-divider orientation="left">文本插值</a-divider>
            <a-form layout="inline" class="content-item">
              <a-form-item label="输入框">
                <a-input v-model="inputContent"></a-input>
              </a-form-item>
              <a-form-item label="输入框内容">
                <label>{{inputContent}}</label>
              </a-form-item>
            </a-form>
          </div>

          <div>
            <a-divider orientation="left">计算属性</a-divider>
            <a-form layout="inline" class="content-item">
              <a-form-item label="输入框">
                <a-input v-model="computedInput"></a-input>
              </a-form-item>
              <a-form-item label="输入框内容">
                <label>{{computedOutput}}</label>
              </a-form-item>
            </a-form>
          </div>

          <div>
            <a-divider orientation="left">v-if 和 v-show</a-divider>
            <a-form layout="inline" class="content-item">
              <a-form-item>
                <a-switch
                  checkedChildren="true"
                  unCheckedChildren="false"
                  v-model="vifShow"
                ></a-switch>
              </a-form-item>

              <a-form-item>
                <label v-if="vifShow">vifShow 值为 true 才渲染并显示</label>
              </a-form-item>
            </a-form>

            <a-form layout="inline" class="content-item">
              <a-form-item>
                <a-switch
                  checkedChildren="true"
                  unCheckedChildren="false"
                  v-model="vshowShow"
                ></a-switch>
              </a-form-item>

              <a-form-item>
                <label v-show="vshowShow">vshowShow 值为 true 才显示</label>
              </a-form-item>
            </a-form>
          </div>

          <div>
            <a-divider orientation="left">v-bind</a-divider>
            <a-form layout="inline" class="content-item">
              <a-form-item>
                <a-input v-model="placeholderContent"></a-input>
              </a-form-item>

              <a-form-item label="将左侧输入的文本绑定为占位符">
                <a-input :placeholder="placeholderContent"></a-input>
              </a-form-item>
            </a-form>
          </div>

          <div>
            <a-divider orientation="left">v-on</a-divider>
            <a-form layout="inline" class="content-item">
              <a-form-item label="输入框事件（回车触发）">
                <a-input
                  @pressEnter="onInputFinish"
                  v-model="inputStr"
                ></a-input>
              </a-form-item>

              <a-form-item label="按钮点击事件">
                <a-button
                  type="primary"
                  @click="onBtnClick"
                >用力点我</a-button>
              </a-form-item>
            </a-form>
          </div>

          <div>
            <a-divider orientation="left">v-for</a-divider>
            <a-form layout="inline" class="content-item">
              <a-form-item label="输入表格内容（换行后新增）">
                <a-textarea v-model="textareaInput"></a-textarea>
              </a-form-item>

              <a-form-item v-if="textareaData.length > 0">
                <a-list
                  v-for="item in textareaData"
                  :key="item.key"
                  size="small"
                  bordered
                >
                  <a-list-item class="list-item">
                    <span>{{ item.value }}</span>
                  </a-list-item>
                </a-list>
              </a-form-item>
            </a-form>
          </div>
        </a-layout-content>

        <!-- <a-layout-footer class="home-footer">Antd-demo 测试例</a-layout-footer> -->
      </a-layout>
    </a-layout>
  </a-layout>
</template>

<script>
export default {
  name: 'home',
  data() {
    return {
      inputContent: '影分身之术',
      computedInput: '如蜜传如蜜',
      vifShow: false,
      vshowShow: false,
      placeholderContent: '(｡･∀･)ﾉﾞ',
      inputStr: '',
      textareaInput: '',
    }
  },
  computed: {
    computedOutput() {
      return this.computedInput.split('').reverse().join('');
    },

    textareaData() {
      const arr = this.textareaInput.split('\n');
      const result = [];
      arr.forEach((item, index) => {
        if (item !== '') {
          result.push({
            index,
            value: item,
          });
        }
      });
      return result;
    },
  },
  methods: {
    onInputFinish() {
      alert(`【报告】输入完毕！输入内容: ${this.inputStr}`);
    },
    onBtnClick() {
      alert('啊~');
    },
  },
}
</script>

<style scoped>
.home-layout {
  margin: 0px;
  width: 100%;
  height: 100%;
}
.home-layout-header {
  padding: 0px;
}
.title-text {
  text-align: center;
  color: white;
  width: 200px;
  font-size: 18px;
  font-weight: bold;
}
.home-footer {
  text-align: center;
}
.content-item {
  margin: 0px 10px;
}
.list-item {
  padding: 0px 0px;
}
</style>
