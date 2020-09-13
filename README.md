# Vue3 cho người mới bắt đàu

Dự án này mong giúp đỡ các bạn newbie có thể học VueJS v3 một cách đơn giản hơn.

## Chương 1 - Directive and Data Rendering

### Tại sao chúng ta lại chọn VueJS

- Rõ ràng
- Đơn giản
- Dễ khai báo
- Dễ bảo trì
- Năng động

### Các loại directive mà chúng ta cần biết

- [v-text](https://vuejs.org/v2/api/#v-text)
  Dùng để render chữ thông thường

- [v-html](https://vuejs.org/v2/api/#v-html)
  Dùng để render ra nội dung là code html

- [v-show](https://vuejs.org/v2/api/#v-show)
  Dùng để render ra nội dung tuỳ thuộc vào điều kiện trong directive là đúng

- [v-if](https://vuejs.org/v2/api/#v-if)
  Dùng để render ra nội dung tuỳ thuộc vào điều kiện trong directive là đúng
- [v-else](https://vuejs.org/v2/api/#v-else)
  Dùng để render ra nội dung tuỳ thuộc vào điều kiện trong directive ở `v-if` là không đúng
- [v-else-if](https://vuejs.org/v2/api/#v-else-if)
  Dùng để render ra nội dung tuỳ thuộc vào điều kiện trong directive ở `v-else-if` là không đúng. Phải dùng chung với `v-if` và `v-else`.

- [v-for](https://vuejs.org/v2/api/#v-for)
  Dùng để lặp qua các phần tử trong directive and render từng phần từ ra

- [v-on](https://vuejs.org/v2/api/#v-on)
  Dùng để đăng ký lắng nghe sự kiện trên element. Viết tắt là `@`, ví dụ như:

  ```js
  <button v-on:click="doThis"></button>
  ```

- [v-bind](https://vuejs.org/v2/api/#v-bind)
  Dùng để tạo liên kết một hoặc nhiều thuộc tính, hoặc props của component bằng biểu thức.
- [v-model](https://vuejs.org/v2/api/#v-model)
  Tạo liên kết hai chiều giữa dữ liệu và thành phần biểu mẫu hoặc compoennt.

- [v-pre](https://vuejs.org/v2/api/#v-pre)
  Dùng việc phiên dịch cho phần tử và tất cả các thành phần con của nó. Bạn nên dùng nó để render ra một số lượng lớn phần tử mà không dùng directives để có thể tăng tốc độ biên dịch.

- [v-cloak](https://vuejs.org/v2/api/#v-cloak)

- [v-once](https://vuejs.org/v2/api/#v-once)
  Dùng để render một lần duy nhất và tránh việc render lại phần tử này sau đó.

### Modifier

Trong nhiều trường hợp chúng ta cần can thiệp vào cách sự kiện xảy ra như `event.preventDefault()` hoặc `event.stopPropagation()`. Để làm các việc này Vue cung cấp cho chúng ta một số **event modifier** để có thể làm các công việc trên thông qua một hậu tố (post-fix) cho directive và được biểu thị bằng một dấu chấm.

- `.stop`
- `.prevent`
- `.capture`
- `.self`
- `.once`

Khi sử dụng nhiều modifier thì thứ tự từ nối rất quan trọng, code sẽ được tạo ra theo đúng thứ tự đó.

## Chương 2 - Methods, Computed, Watchers

### Methods - Hàm

Đây là một thành phần quan trọng được liên kết với đối tượng Vue. Các method này dùng để truy cập vào các thông tin directives.

### Computed

Các thuộc tính được tính toán và lưu trữ lại kết quả và nó chỉ thay đổi và tính toán lại khi cần thiết. Computed có độ thực thi cực kỳ tốt nhưng nên sử dụng một cách có hiểu biết.

| #### Computed | ### Methods |
| Thay đổi khi các thuộc tính phụ thuộc thay đổi | Chạy mỗi khi có thay đổi |
| Cached | Not cached |
| Sử dụng giống như thuộc tính data | Phần lớn sử dụng với v-on/@ nhưng khá linh hoạt |
| Thương là có hàm getter mặc định, nhưng có thể thêm setter | Có cả Getter/setter |

### Watcher

Đây là một thứ quan trọng trong VueJS. Watcher giúp bạn quan sát và cập nhật các sự kiện xảy ra cho dữ liệu bất đồng bộ. Khi bạn watch một giá trị, bạn có thể trigger một sự kiện khi mà giá trị đó thay đổi.

```
watch: { watchedProperty (value, oldValue) {
  //your dope code here
}
```

Bạn cũng có thể quan sát gía trị nằm trong thuộc tính bạn quan sát với giá trị `deep`.

```
watch: {
  watchedProperty {
    deep: true,
    nestedWatchedProperty (value, oldValue) {
      //your code here
    }
  }
},
```

## Chương 3 - Components

### TEMPLATES

Vue.js dùng định dạng và cú pháp HTML để gắn kết giữa đối tượng Vue và DOM, việc này rất có ích cho các thành phần (component).

Nếu bạn không muốn sử dụng template, bạn có thể sử dụng trực tiếp hàm render và cú pháp JSX.

### COMPONENTS

Là tập hợp các thành phần nhỏ hơn được gói gọn lại trong một nhóm và được truy cập thông qua tên nhóm của chúng.

```JSX
<div>
  <p></p>
  <div></div>
  <p></p>
  <small></small>
</div>

<hello></hello>
```

### PROPS

Dùng để truyền dữ liệu từ cha xuống con.
Props được sử dụng theo hướng truyền dữ liệu một chiều.

#### TYPES & VALIDATION

```js
props: {
  text: [String, Number];
}
```

```
Vue.component('child', {
  props: {
    text: {
      type: String,
      required: true,
      default: 'hello mr. magoo'
    }
  },
  template: `<div>{{ text }}<div>`
});
```

Bạn có thể truyền dữ liệu tĩnh hoặc dữ liệu động cho đối tượng con.

```
  <h4><app-child count="3"></app-child></h4>  <= this is binding static props
  <h4><app-child :count="count"></app-child></h4> <= this is binding dynamic props
```

### DATA

Data phải là một hàm trả về trong VueJS.

```js
const app = Vue.createApp({
  data() {
    return {
      manifest: [
        {
          item: "backpack",
          url: "https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/backpack.jpg"
        },
        {
          item: "tshirt",
          url: "https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/tshirt.jpg"
        },
         {
          item: "sweatshirt",
          url: "https://s3-us-west-2.amazonaws.com/s.cdpn.io/28963/sweatshirt.jpg"
        },
      ]
    };
  }
})

<div id="app">
  <div class="unit" v-for="unit in manifest" :key="unit.item">
    <app-child :item="unit.item" :url="unit.url"></app-child>
  </div>
</div>

app.component('app-child', {
  template: '#child',
  props: ['item', 'url'],
  data() {
    return {
      counter: 0
    }
  }
})


<div class="item">
  <h2>{{ item }}</h2>
  <img :src="url" width="235" height="300"/>
  <div class="quantity">
    <button class="inc" @click="counter > 0 ? counter -= 1 : 0">-</button>
    <span class="quant-text">Quantity: {{ counter }}</span>
    <button class="inc" @click="counter += 1">+</button>
  </div>
  <button class="submit">Submit</button>
</div><!--item-->
```

### COMMUNICATIONS EVENTS

Bạn cần dùng Emit để có thể giao tiếp thành phần con và cha. Emit là cách hiện tại duy nhất, chúng ta sẽ biết các cách khác thông qua Vuex và Composition API.

Thành phần con sẽ báo các hoạt động cho thành phần cha bằng sự kiện emit.

```JSX
<my-component @myevent="parentHandler">
  <button @click="$emit('myevent')"></button>
  <button @click="$emit('myevent', param)"></button>
</my-component>
```

### SLOTS

Bạn có thể dùng slot để đục lỗ sẵn các đối tượng để sau này có thể thay đổi dữ liệu sau đó.

```js
<script type="text/x-template" id="childarea">
  <div class="child">
    <slot></slot>
    <p>It's a veritable slot machine!<br>
    Ha ha aw</p>
  </div>
</script>
```

```js
<div id="app">
  <h2>We can use slots to populate content</h2>
  <app-child>
    <h3>This is slot number one</h3>
  </app-child>
  <app-child>
    <h3>This is slot number two</h3>
    <small>I can put more info in, too!</small>
  </app-child>
</div>
```

Bạn cũng có thể có giá trị mặc định cho slot.

```js
<slot>I am some default text</slot>
```

## Chương 4 - Vue CLI

### Tại sao nên dùng Vue Commandline

- Quy trình build dễ dàng sử dụng với các chức năng nâng cao như ES6, SCSS và có thể sử dụng chung với các thư viện khác.
- Chúng ta sẽ tập trung vào single file templates - nghĩa là một file tất cả trong một.
- Không load tất cả mọi thứ một lần lúc khởi động (lazy load và chạy bất đồng bộ)
- Server-side redering - render từ phía server, code theo từ mục riêng lẻ, có chỉ số cao
- Có thể build bản production.

#### Single file template

```js
<template>
  <div>
     <!-- Write your HTML with Vue in here -->
  </div>
</template>

<script>
  export default {
     // Write your Vue component logic here
  }
</script>

<style scoped>
  /* Write your styles for the component in here */
</style>
```

```js
import New from './components/New.vue';

export default {
  components: {
    appNew: New
  }
}
<app-new></app-new> <= the compoenent will be like this
```

## snippets save lives

- [vue-vscode-snippets](https://marketplace.visualstudio.com/items?itemName=sdras.vue-vscode-snippets)
- [vue-sublime-snippets](https://github.com/sdras/vue-sublime-snippets)
- [atom (v 1.x)](https://atom.io/packages/vue-snippets)
- [Vetur for vscode](https://marketplace.visualstudio.com/items?itemName=octref.vetur)

```
<style scoped>
```

⇒ Cho phép chúng ta chỉ sử dụng style cho component này.

Các import css một cách tổng quát toàn dự án - https://css-tricks.com/how-to-import-a-sass-file-into-every-vue-component-in-an-app/

### Lifecycle hook - Vòng đời

- [beforeCreate](https://v3.vuejs.org/api/options-lifecycle-hooks.html#beforecreate)
- [created](https://v3.vuejs.org/api/options-lifecycle-hooks.html#created) - great place to call APIs
- [beforeMount](https://v3.vuejs.org/api/options-lifecycle-hooks.html#beforemount)
- [mounted](https://v3.vuejs.org/api/options-lifecycle-hooks.html#mounted) - great place to work on DOM operations
- [beforeUpdate](https://v3.vuejs.org/api/options-lifecycle-hooks.html#beforeupdate)
- [updated](https://v3.vuejs.org/api/options-lifecycle-hooks.html#updated)
- [activated](https://v3.vuejs.org/api/options-lifecycle-hooks.html#activated) - associated for keep-alive
- [deactivated](https://v3.vuejs.org/api/options-lifecycle-hooks.html#deactivated)
- [beforeUnmount](https://v3.vuejs.org/api/options-lifecycle-hooks.html#beforeunmount) (was beforeDestroy v2)
- [unmounted](https://v3.vuejs.org/api/options-lifecycle-hooks.html#unmounted) (was destroyed v2)
- [errorCaptured](https://v3.vuejs.org/api/options-lifecycle-hooks.html#errorcaptured) - (new! v3)
- [renderTracked](https://v3.vuejs.org/api/options-lifecycle-hooks.html#rendertracked) - (new! v3) when vDOM is rerendered, good for debugging
- [renderTriggered](https://v3.vuejs.org/api/options-lifecycle-hooks.html#rendertriggered) - (new! v3)similar, but tells you what triggered the rerendering

```js
const Child = {
  template: '#childarea',
  beforeCreate() {
    console.log("beforeCreate!");
  },
 ...
};

new Vue({
  el: '#app',
  data() {
    return {
      isShowing: false
    }
  },
  methods: {
    toggleShow() {
      this.isShowing = !this.isShowing;
    }
  },
  components: {
    appChild: Child
  }
});
```

Vòng đời hook được tự động gắn vào mỗi đối tượng Vue để bạn có thể sử dụng các chức năng của thành phần như state, method. Bạn không nên sử dụng arrow function trong các method liên quan tới vòng đời vì nó sẽ trả về cha thay vì gắn vào đối tượng Vue như bạn mong đợi.

## nuxt & routing

Các điểm đặc biệt về nuxt

- Code tự động được phân chia
- Server side Rendering
- Có hệ thống routing xịn hoạt động tốt với dữ liệu bất đồng bộ
- Có chỉ số tốt khi sử dụng với Google Light House
- Cho phép cung cấp file tĩnh (đã được biên soạn trước)
- Hổ trợ ES6/ES7
- Hot reloading khi đang phát triển
- Hổ trọ xử lý CSS như SASS, LESS, stylus, v.v...
- Hổ trợ viết các file vue

## Chương 5 - Filters, Mixins, & custom Directives

### Filters

- Đầu tiên bạn phải hiểu là filters không thay thế cho hàm - methods, các giá trị computed, hoặc watchers. Filters không thay đổi giá trị của data mà chỉ thay đổi cách xuất ra giá trị cho người dùng xem.

Sau đây là hai cách đăng ký filters mới:

```js
//global
Vue.filter("filterName", function (value) {
  return; // trả về dữ liệu biến đổi
});
```

```js
//locally, like methods or computed
filters: {
  filterName(value) {
    return // trả về dữ liệu biến đổi
  }
}
```

Khi đó bạn có thể sử dụng như thế này

```js
{
  {
    data | filter;
  }
}
///--------------------
{
  {
    text | capitalize;
  }
}
```

Ví dụ cụ thể

```js
new Vue({
  el: '#app',
  data() {
    return {
      customer1total: 35.43
    }
  },
  filters: {
    tip15(value) {
      return (value*.15).toFixed(2)
    },
    ...
  }
}
```

Cách sử dụng trong HTML

```html
<div id="app">
  <h2>Tip Calculator</h2>
  <p><strong>Total: {{ customer1total }}</strong></p>
  <p>15%: {{ customer1total | tip15 }}</p>
  ...
</div>
```

#### Bạn có thể sử dụng nhiều tham số cho filters

```js
{
  {
    data | filterName(arg1, arg2);
  }
}
```

```js
// arguments are passed in order after the value
filters: {
  filterName(value, arg1, arg2) {
    return //thing to transform
  }
}
```

Filter sẽ tốt nếu bạn cần chuyển đổi số lượng lớn dữ liệu hoặc công việc lặp đi lặp lại. Nếu chỉ sử dụng cho 1 trường hợp thì bạn nên sử dụng computed, dữ liệu mà nên cached lại.

## Mixings

Trong trường hợp thông thường bạn có hai component mà chức năng gần giống hệt như nhau. Chúng có chung một số chức năng nhưng có một số khác biệt nhất định. Bạn sẽ đứng giữa quyết định là tạo hai component riêng biệt hay tạo biến với props để làm cho chúng khác nhau.

Có một cách để giải quyết trường hợp này gọi là mixin. Một mixin là cách bạn tách một phần chức năng bạn muốn sử dụng trong component khác thông qua ứng dụng. Nếu sử dụng một cách hợp lý bạn sẽ không cần phải điều chỉnh gì thêm và các component sẽ nhận được giá trị như nhau dù chạy ở các component khác nhau.

````js
//modal
const Modal = {
  template: '#modal',
  data() {
    return {
      isShowing: false
    }
  },
  methods: {
    toggleShow() {
      this.isShowing = !this.isShowing;
    }
  },
  components: {
    appChild: Child
  }
}```

```js
//tooltip
const Tooltip = {
  template: '#tooltip',
  data() {
    return {
      isShowing: false
    }
  },
  methods: {
    toggleShow() {
      this.isShowing = !this.isShowing;
    }
  },
  components: {
    appChild: Child
  }
}
````

#### Refactor to

```js
const toggle = {
  data() {
    return {
      isShowing: false,
    };
  },
  methods: {
    toggleShow() {
      this.isShowing = !this.isShowing;
    },
  },
};

const Modal = {
  template: "#modal",
  mixins: [toggle],
  components: {
    appChild: Child,
  },
};

const Tooltip = {
  template: "#tooltip",
  mixins: [toggle],
  components: {
    appChild: Child,
  },
};
```

### Cách thức code sẽ được merge với mixin

Mặc định, mixin sẽ được áp dụng trước sau đó component sẽ được áp dụng thứ hai sau đó để chúng ta có thể ghi đè.

Component mặc định là người cuối cùng lên tiếng hay có khả năng ghi đè lên tất cả còn lại.

```js
//mixin
const hi = {
  mounted() {
    console.log("hello from mixin!");
  },
};

//vue instance or component
new Vue({
  el: "#app",
  mixins: [hi],
  mounted() {
    console.log("hello from Vue instance!");
  },
});

//Output in console
//> hello from mixin!
//> hello from Vue instance!
```

#### OVERWRITE

```js
//mixin
const hi = {
  methods: {
    sayHello: function () {
      console.log("hello from mixin!");
    },
  },
  mounted() {
    this.sayHello();
  },
};

//vue instance or component
new Vue({
  el: "#app",
  mixins: [hi],
  methods: {
    sayHello: function () {
      console.log("hello from Vue instance!");
    },
  },
  mounted() {
    this.sayHello();
  },
});

// Output in console
//> hello from Vue instance!
//> hello from Vue instance!
```

#### GLOBAL MIXINS

Global mixins là loại mixins mà bạn có thể sử dụng cho tất cả các component. Trường hợp tốt nhất bạn có thể nghĩ tới như là một plugin, bạn có thể gọi từ bất cứ component nào.

> Bạn nên biết rằng global mixins rất mạnh mẽ nhưng phải xài một cách cực kỳ cẩn thận.

#### CUSTOM DIRECTIVES - Directives nhà trồng

- Phần này hơi phức tạp chắc sẽ quay lại sau

## Chương 6 - Vuex

### WHAT - Nó là cái gì

- Là nơi tập trung để chia sẽ data và logic cho app của bạn, kể các các methods hoặc các hàm async
- Unidirectional data flow hay dữ liệu đi theo một hướng View-Action-State theo cách mình định hướng
- Dựa trên kiến trúc của Flux
- Hoạt động tương tự như Redux

### WHY - Tại sao nên dùng nó nhỡ?

- Trong một ứng dụng một trang (SPA) phức tạp, việc truyền dữ liệu giữa các components đôi khi sẽ làm ứng dụng bạn trở nên phức tạp khá nhanh. Việc tập trung dữ liệu lại một chỗ sẽ giúp bạn truy cập cũng như tổ chức code, dữ liệu một cách có trật tự hơn.

### WHEN - Khi nào thì mình nên gắn Vuex vào?

Có thể là bạn sẽ tự nhân ra hoặc có quá nhiều componet con hoặc anh/chị/em đang cố gáng nói chuyện với nhau.
