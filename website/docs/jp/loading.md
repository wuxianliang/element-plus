## ローディング

データ読み込み中にアニメーションを表示する。

### コンテナ内でのローディング

データの読み込み中にコンテナ（テーブルなど）にアニメーションを表示します。

:::demo 要素にはローディングを呼び出すための 2 つの方法があります: ディレクティブとサービスです。カスタムディレクティブ `v-loading` の場合は、`boolean` の値をバインドするだけです。デフォルトでは、ローディングマスクはディレクティブが使われている要素に追加されます。`body` 修飾子を追加すると、マスクは body 要素に追加されます。

```html
<template>
  <el-table v-loading="loading" :data="tableData" style="width: 100%">
    <el-table-column prop="date" label="Date" width="180"> </el-table-column>
    <el-table-column prop="name" label="Name" width="180"> </el-table-column>
    <el-table-column prop="address" label="Address"> </el-table-column>
  </el-table>
</template>

<style>
  body {
    margin: 0;
  }
</style>

<script>
  export default {
    data() {
      return {
        tableData: [
          {
            date: '2016-05-02',
            name: 'John Smith',
            address: 'No.1518,  Jinshajiang Road, Putuo District',
          },
          {
            date: '2016-05-04',
            name: 'John Smith',
            address: 'No.1518,  Jinshajiang Road, Putuo District',
          },
          {
            date: '2016-05-01',
            name: 'John Smith',
            address: 'No.1518,  Jinshajiang Road, Putuo District',
          },
        ],
        loading: true,
      }
    },
  }
</script>
<!--
<setup>

import { defineComponent, reactive, toRefs } from 'vue';

export default defineComponent({
  setup() {
    const state = reactive({
      tableData: [
        {
          date: '2016-05-02',
          name: 'John Smith',
          address: 'No.1518,  Jinshajiang Road, Putuo District',
        },
        {
          date: '2016-05-04',
          name: 'John Smith',
          address: 'No.1518,  Jinshajiang Road, Putuo District',
        },
        {
          date: '2016-05-01',
          name: 'John Smith',
          address: 'No.1518,  Jinshajiang Road, Putuo District',
        },
      ],
      loading: true,
    });
    return {
      ...toRefs(state),
    };
  },
});

</setup>
-->
```

:::

### カスタマイズ

ローディングテキスト、ローディングスピナー、背景色をカスタマイズすることができます。

:::demo `v-loading` がバインドされている要素に `element-loading-text` 属性を追加すると、その値がスピナの下に表示されるようになります。同様に、 `element-loading-spinner`、` element-loading-background`、および `element-loading-svg`属性は、それぞれアイコンクラス名、背景色の値、および読み込みアイコンを設定するために使用されます。

```html
<template>
  <el-table
    v-loading="loading"
    element-loading-text="Loading..."
    element-loading-spinner="el-icon-loading"
    element-loading-background="rgba(0, 0, 0, 0.8)"
    :data="tableData"
    style="width: 100%"
  >
    <el-table-column prop="date" label="Date" width="180"> </el-table-column>
    <el-table-column prop="name" label="Name" width="180"> </el-table-column>
    <el-table-column prop="address" label="Address"> </el-table-column>
  </el-table>
  <el-table
    v-loading="loading"
    :element-loading-svg="svg"
    class="custom-loading-svg"
    element-loading-svg-view-box="-10, -10, 50, 50"
    :data="tableData"
    style="width: 100%"
  >
    <el-table-column prop="date" label="Date" width="180"> </el-table-column>
    <el-table-column prop="name" label="Name" width="180"> </el-table-column>
    <el-table-column prop="address" label="Address"> </el-table-column>
  </el-table>
</template>

<style>
  .custom-loading-svg .el-loading-mask > .el-loading-spinner > .circular {
    animation: none;
  }
</style>

<script>
  export default {
    data() {
      return {
        tableData: [
          {
            date: '2016-05-02',
            name: 'John Smith',
            address: 'No.1518,  Jinshajiang Road, Putuo District',
          },
          {
            date: '2016-05-04',
            name: 'John Smith',
            address: 'No.1518,  Jinshajiang Road, Putuo District',
          },
          {
            date: '2016-05-01',
            name: 'John Smith',
            address: 'No.1518,  Jinshajiang Road, Putuo District',
          },
        ],
        loading: true,
        svg: `
          <path class="path" d="
            M 30 15
            L 28 17
            M 25.61 25.61
            A 15 15, 0, 0, 1, 15 30
            A 15 15, 0, 1, 1, 27.99 7.5
            L 15 15
          " style="stroke-width: 4px; fill: rgba(0, 0, 0, 0)"/>
        `,
      }
    },
  }
</script>
<!--
<setup>

import { defineComponent, reactive, toRefs } from 'vue';

export default defineComponent({
  setup() {
    const state = reactive({
      tableData: [
        {
          date: '2016-05-02',
          name: 'John Smith',
          address: 'No.1518,  Jinshajiang Road, Putuo District',
        },
        {
          date: '2016-05-04',
          name: 'John Smith',
          address: 'No.1518,  Jinshajiang Road, Putuo District',
        },
        {
          date: '2016-05-01',
          name: 'John Smith',
          address: 'No.1518,  Jinshajiang Road, Putuo District',
        },
      ],
      loading: true,
      svg: `
        <path class="path" d="
          M 30 15
          L 28 17
          M 25.61 25.61
          A 15 15, 0, 0, 1, 15 30
          A 15 15, 0, 1, 1, 27.99 7.5
          L 15 15
        " style="stroke-width: 4px; fill: rgba(0, 0, 0, 0)"/>
      `,
    });
    return {
      ...toRefs(state),
    };
  },
});

</setup>
-->
```

:::

:::warning
`element-loading-svg`属性は受信 HTML フラグメントをサポートしますが、[XSS 攻撃](https://en.wikipedia.org/wiki/Cross-site_scripting)を引き起こしやすいため、Web サイトで任意の HTML を動的にレンダリングすることは非常に危険です。）。 `element-loading-svg`のコンテンツが信頼できるものであることを確認してください。\*\*ユーザーが送信したコンテンツを` element-loading-svg`属性に割り当てないでください。
:::

### 全画面読み込み

データの読み込み中に全画面アニメーションを表示します。

:::demo ディレクティブとして使われる場合、フルスクリーンの読み込みには `fullscreen` 修飾子が必要で、それがボディに追加されます。この場合、ボディ上でのスクロールを無効にしたい場合は、別の修飾子 `lock` を追加します。サービスとして利用される場合、Loading はデフォルトで全画面表示になります。

```html
<template>
  <el-button
    type="primary"
    @click="openFullScreen1"
    v-loading.fullscreen.lock="fullscreenLoading"
  >
    As a directive
  </el-button>
  <el-button type="primary" @click="openFullScreen2"> As a service </el-button>
</template>

<script>
  export default {
    data() {
      return {
        fullscreenLoading: false,
      }
    },
    methods: {
      openFullScreen1() {
        this.fullscreenLoading = true
        setTimeout(() => {
          this.fullscreenLoading = false
        }, 2000)
      },
      openFullScreen2() {
        const loading = this.$loading({
          lock: true,
          text: 'Loading',
          spinner: 'el-icon-loading',
          background: 'rgba(0, 0, 0, 0.7)',
        })
        setTimeout(() => {
          loading.close()
        }, 2000)
      },
    },
  }
</script>
<!--
<setup>

  import { defineComponent, ref } from 'vue';
  import { ElLoading } from 'element-plus';

  export default defineComponent({
    setup() {
      const fullscreenLoading = ref(false);
      const openFullScreen1 = () => {
        fullscreenLoading.value = true;
        setTimeout(() => {
          fullscreenLoading.value = false;
        }, 2000);
      };

      const openFullScreen2 = () => {
        const loading = ElLoading.service({
          lock: true,
          text: 'Loading',
          spinner: 'el-icon-loading',
          background: 'rgba(0, 0, 0, 0.7)',
        });
        setTimeout(() => {
          loading.close();
        }, 2000);
      };

      return {
        fullscreenLoading,
        openFullScreen1,
        openFullScreen2,
      };
    },
  });

</setup>
-->
```

:::

### サービス

サービスで Loading を呼び出すこともできます。Loading サービスをインポートします:

```javascript
import { ElLoading } from 'element-plus'
```

呼び出す:

```javascript
ElLoading.service(options)
```

パラメータ `options` は Loading の設定であり、その詳細は以下の表にある。LoadingService`はLoadingのインスタンスを返し、その`close` メソッドを呼び出すことでインスタンスを閉じることができる。:

```javascript
let loadingInstance = ElLoading.service(options)
this.$nextTick(() => {
  // Loading should be closed asynchronously
  loadingInstance.close()
})
```

フルスクリーン Loading はシングルトンであることに注意してください。既存のフルスクリーン Loading がクローズされる前に新しいフルスクリーン Loading が呼び出された場合、実際に別の Loading インスタンスを作成するのではなく、既存のフルスクリーン Loading インスタンスが返されます。:

```javascript
let loadingInstance1 = ElLoading.service({ fullscreen: true })
let loadingInstance2 = ElLoading.service({ fullscreen: true })
console.log(loadingInstance1 === loadingInstance2) // true
```

これらのいずれかで`close` メソッドを呼び出すことで、このフルスクリーンの読み込みを閉じることができる。

Element Plus を完全にインポートしている場合は、Vue.prototype にグローバルメソッド `$loading` が登録されます。このように呼び出すことができます。このメソッドは、`this.$loading(options)`のように呼び出すことができます。

### Options

| Attribute   | Description                                                                                                                                                                        | Type          | Accepted Values | Default       |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | --------------- | ------------- |
| target      | コンポーネントがカバーしなければならない DOM ノード。DOM オブジェクトまたは文字列を受け付けます。文字列の場合は document.querySelector に渡され、対応する DOM ノードを取得します。 | object/string | —               | document.body |
| body        | `v-loading` の `body` 修飾子と同じです。                                                                                                                                           | boolean       | —               | false         |
| fullscreen  | `v-loading` の `fullscreen` 修飾子と同じです。                                                                                                                                     | boolean       | —               | true          |
| lock        | `v-loading` の `lock` 修飾子と同じです。                                                                                                                                           | boolean       | —               | false         |
| text        | スピナーの下に表示されるローディングテキスト                                                                                                                                       | string        | —               | —             |
| spinner     | カスタムスピナーのクラス名                                                                                                                                                         | string        | —               | —             |
| background  | マスクの背景色                                                                                                                                                                     | string        | —               | —             |
| customClass | ローディングのカスタムクラス名                                                                                                                                                     | string        | —               | —             |
