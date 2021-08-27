---
title: Vuex
date: 2021-07-31 20:24:20
updated:
tags:
  - Vue
  - vuex
categories:
  - Vue
  - Vue脚手架
keywords:
description:
top_img: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/csslayouts/sunrise.jpg
cover: https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vue/vuex.png
comments:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
---

# Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式

- `state` , 驱动应用的数据源
- `view` , 以声明方式将 state 映射到视图
- `actions` , 响应在 view 上的用户输入导致的状态变化

**以下是一个表示“单向数据流”理念的简单示意**
![state_view_actions](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vuebasic/vuexstate.png)

但是 , 当我们的应用遇到多个组件共享状态时 , 单向数据流的简洁性很容易被破坏 :

- 多个视图依赖于同一状态
- 来自不同视图的行为需要变更同一状态

![vuex](https://codehhr.coding.net/p/codehhr/d/images/git/raw/master/vuebasic/vuex.png)

# 核心概念

# State

## 在 `Vue` 组件中获得 `Vuex` 状态

```js
// 比如创建一个组件
const componentA = {
  template: `<div>{{ valueA }}</div>`,
  computed: {
    valueA() {
      return store.state.valueA;
    },
  },
};
```

每当 `store.state.valueA` 变化的时候, 都会重新求取计算属性 , 并且触发更新相关联的 `DOM`

然而 , 这种模式导致组件依赖全局状态单例 ,在模块化的构建系统中 , 在每个需要使用 `state` 的组件中需要频繁地导入 , 并且在测试组件时需要模拟状态。

`Vuex` 通过 `store` 选项 , 提供了一种机制将状态从根组件 `注入` 到每一个子组件中 ( 需调用 `Vue.use(Vuex)` )

```js
const app = new Vue({
  el: "#app",
  // 把 store 对象提供给 "store" 选项 , 这可以把 store 的实例注入所有的子组件
  store,
  components: { componentA },
  template: `
    <div class="app">
      <componentA></componentA>
    </div>
  `,
});
```

### mapState 辅助函数

当一个组件需要获取多个状态的时候 , 将这些状态都声明为计算属性会有些重复和冗余 , 为了解决这个问题 , 我们可以使用 `mapState` 辅助函数帮助我们生成计算属性

```js
import { mapState } from "vuex";
export default {
  computed: {
    ...mapState({
      valueA: "valueA",
    }),
  },
};
```

# Getter

有时候我们需要从 `store` 中的 `state` 中派生出一些状态 , 例如对列表进行过滤并计数:

```js
computed: {
  doneTodosCount () {
    return this.$store.state.todos.filter(todo => todo.done).length
  }
}
```

`Vuex` 允许我们在 `store` 中定义 `getter` ( 可以认为是 `store` 的计算属性 ) , 就像计算属性一样 , `getter` 的返回值会根据它的依赖被缓存起来 , 且只有当它的依赖值发生了改变才会被重新计算

`Getter` 接受 `state` 作为其第一个参数 :

```js
const store = new Vuex.Store({
  state: {
    todos: [
      { id: 1, text: "...", done: true },
      { id: 2, text: "...", done: false },
    ],
  },
  getters: {
    doneTodos: (state) => {
      return state.todos.filter((todo) => todo.done);
    },
  },
});
```

### mapGetters 辅助函数

`mapGetters` 辅助函数仅仅是将 `store` 中的 `getter` 映射到局部计算属性

```js
import { mapGetters } from "vuex";

export default {
  computed: {
    // 使用对象展开运算符将 getter 混入 computed 对象中
    ...mapGetters([
      "doneTodosCount",
      "anotherGetter",
      // ...
    ]),
  },
};
```

如果你想将一个 `getter` 属性另取一个名字 , 使用对象形式 :

```js
...mapGetters({
  // 把 `this.doneCount` 映射为 `this.$store.getters.doneTodosCount`
  doneCount: 'doneTodosCount'
})
```

# Mutation

更改 `Vuex` 的 `store` 中的状态的唯一方法是提交 `mutation`

## 提交载荷( `Payload` )

你可以向 `store.commit` 传入额外的参数 , 即 `mutation` 的 载荷 ( `payload ) :

```js
this.$store.commit("increment", payload);
```

在大多数情况下 , 载荷应该是一个对象 , 这样可以包含多个字段并且记录的 `mutation` 会更易读 :

```js
store.commit("increment", { amount: 10 });
```

```js
// ...
mutations: {
  increment (state, payload) {
    state.count = payload.amount
  }
}
```

# Action

`Action` 类似于 `mutation` , 不同在于 :

- `Action` 提交的是 `mutation` , 而不是直接变更状态
- `Action` 可以包含任意异步操作

`Action` 函数接受一个与 `store` 实例具有相同方法和属性的 `context` 对象 , 因此你可以调用 `context.commit` 提交一个 `mutation` , 或者通过 `context.state` 和 `context.getters` 来获取 `state` 和 `getters`

```js
actions: {
  increment (context,payload) {
     context.commit('increment',payload)
  }
}
```

乍一眼看上去感觉多此一举 , 我们直接分发 `mutation` 岂不更方便 ? 实际上并非如此 , 还记得 `mutation` 必须同步执行这个限制么 ? `Action` 就不受约束 ! 我们可以在 `action` 内部执行异步操作 :

```js
actions: {
  increment (context,payload) {
    setTimeout(() => {
      context.commit('increment',payload)
    }, 1000)
  }
}
```

`Actions` 支持同样的载荷方式和对象方式进行分发 :

```js
// 以载荷形式分发
this.$store.dispatch("incrementAsync", {
  amount: 10,
});
```

```js
// 以对象形式分发
this.$store.dispatch({
  type: "incrementAsync",
  amount: 10,
});
```

# Module

由于使用单一状态树 , 应用的所有状态会集中到一个比较大的对象 , 当应用变得非常复杂时 , `store` 对象就有可能变得相当臃肿
为了解决以上问题 , `Vuex` 允许我们将 `store` 分割成模块 ( `module` ) , 每个模块拥有自己的 `state`、`mutation`、`action`、`getter`、甚至是嵌套子模块——从上至下进行同样方式的分割:

```js
const moduleA = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... },
  getters: { ... }
}

const moduleB = {
  state: () => ({ ... }),
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

store.state.a // -> moduleA 的状态
store.state.b // -> moduleB 的状态
```

## 模块的局部状态

对于模块内部的 `mutation` 和 `getter` , 接收的第一个参数是模块的局部状态对象

```js
const moduleA = {
  state: () => ({
    count: 0,
  }),
  mutations: {
    increment(state) {
      // 这里的 `state` 对象是模块的局部状态
      state.count++;
    },
  },

  getters: {
    doubleCount(state) {
      return state.count * 2;
    },
  },
};
```

同样 , 对于模块内部的 action , 局部状态通过 `context.state` 暴露出来 , 根节点状态则为 `context.rootState` :

```js
const moduleA = {
  // ...
  actions: {
    incrementIfOddOnRootSum({ state, commit, rootState }) {
      if ((state.count + rootState.count) % 2 === 1) {
        commit("increment");
      }
    },
  },
};
```

## 命名空间

如果希望你的模块具有更高的封装度和复用性 , 你可以通过添加 `namespaced`: `true` 的方式使其成为带命名空间的模块。当模块被注册后 , 它的所有 `getter`、`action` 及 `mutation` 都会自动根据模块注册的路径调整命名 ,例如 :

```js
const store = new Vuex.Store({
  modules: {
    account: {
      namespaced: true,

      // 模块内容（module assets）
      state: () => ({ ... }), // 模块内的状态已经是嵌套的了 , 使用 `namespaced` 属性不会对其产生影响
      getters: {
        isAdmin () { ... } // -> getters['account/isAdmin']
      },
      actions: {
        login () { ... } // -> dispatch('account/login')
      },
      mutations: {
        login () { ... } // -> commit('account/login')
      },

      // 嵌套模块
      modules: {
        // 继承父模块的命名空间
        myPage: {
          state: () => ({ ... }),
          getters: {
            profile () { ... } // -> getters['account/profile']
          }
        },

        // 进一步嵌套命名空间
        posts: {
          namespaced: true,

          state: () => ({ ... }),
          getters: {
            popular () { ... } // -> getters['account/posts/popular']
          }
        }
      }
    }
  }
})
```
