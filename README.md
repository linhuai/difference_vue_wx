# Vue 和 小程序 的差异

**一、条件渲染**

　　**vue** 使用 v-if 指令; 

　　v-else 表示 v-if 的 else 块，v-else-if 表示 v-if 的 else-if 块;

　　**小程序**使用 wx:if;

　　wx:else 表示 wx:if 的 else 块，wx:elif 表示 wx:if 的 else-if 块

	// vue
	<div v-if="type == 'a'"> a </div>
	<div v-else-if="type == 'b'"> b </div>
	<div v-else> not a/b</div>

	//小程序
	<view wx:if="{{type == 'a'}}"> a </view>
	<view wx:elif="{{type == 'b'}}"> b </view>
	<view wx:else> not a/b </view>

**二、显示/隐藏元素**

　　Vue: v-show="..."

　　小程序: hidden="{{...}}"

**三、绑定值**

　　vue: 动态绑定一个变量的值为元素的某个属性的时候，会在变量前面加上冒号:,例如：<img :src="imgSrc" />

　　小程序: 绑定某个变量的值为某个元素属性时，会用两个大括号括起来，例如：<image src="{{imgSrc}}" ></image>

**四、事件处理**

　　vue：使用 v-on:event 绑定事件，或者用 @event 绑定事件

	<button v-on:click="counter += 1">Add 1</button>
	<button v-on:click.stop="counter +=1 "> Add 1 </button> // 阻止冒泡
	<button v-on:click.prevent="counter += 1"> Add 1 </button> //取消默认事件

　　小程序：全用binttap(bind+event), 或者 catchbind(catch+event) 绑定事件

	<button bindtap="clickme">点击我</button>
	<button catchtap="clickme">点击我</button> // 阻止冒泡

**五、绑定事件传参**

　　vue: 绑定事件的函数传参数时，可以把参数写在函数后面的括号里

	<div @click="changeTag(1)">foo</div>

　　微信小程序：事件函数只能传函数名，函数值可以绑定到元素中，例如：data-val=''

	<view data-tab="1" catchtap="changeTab">哈哈</view>
	changeTab(e) {
		var _tab = e.currentTarget.dataset.tab
	}

**六、设置值**

　　vue: 设置 foo 的值可以用，this.foo = true; 获取 foo 的值用 this.foo
　　
　　小程序：设置 foo 的值用 this.setData({foo: true}); 获取 foo 的值用 this.data.foo