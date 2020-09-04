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

- Chương 3 - Components
- Chương 4 - Vue CLI
- Chương 5 - Filters, Mixins, & custom Directives
- Chương 6 - Vuex
