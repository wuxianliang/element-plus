## Radio

Single selection among multiple options.

### Basic usage

Radio should not have too many options. Otherwise, use the Select component instead.

:::demo Creating a radio component is easy, you just need to bind a variable to Radio's `v-model`. It equals to the value of `label` of the chosen radio. The type of `label` is `String`, `Number` or `Boolean`.

```html
<template>
  <div>
    <el-radio v-model="radio1" label="1">Option 1</el-radio>
    <el-radio v-model="radio1" label="2">Option 2</el-radio>
  </div>
  <div>
    <el-radio v-model="radio2" label="1" size="medium">Option 1</el-radio>
    <el-radio v-model="radio2" label="2" size="medium">Option 2</el-radio>
  </div>
  <div>
    <el-radio v-model="radio3" label="1" size="small">Option 1</el-radio>
    <el-radio v-model="radio3" label="2" size="small">Option 2</el-radio>
  </div>
  <div>
    <el-radio v-model="radio4" label="1" size="mini">Option 1</el-radio>
    <el-radio v-model="radio4" label="2" size="mini">Option 2</el-radio>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        radio1: '1',
        radio2: '1',
        radio3: '1',
        radio4: '1',
      }
    },
  }
</script>
<!--
<setup>
  import { defineComponent, ref } from 'vue'

  export default defineComponent({
    setup() {
      return {
        radio1: ref('1'),
        radio2: ref('1'),
        radio3: ref('1'),
        radio4: ref('1'),
      }
    }
  })
</setup>
-->
```

:::

### Disabled

`disabled` attribute is used to disable the radio.

:::demo You just need to add the `disabled` attribute.

```html
<template>
  <el-radio disabled v-model="radio" label="disabled">Option A</el-radio>
  <el-radio disabled v-model="radio" label="selected and disabled"
    >Option B</el-radio
  >
</template>

<script>
  export default {
    data() {
      return {
        radio: 'selected and disabled',
      }
    },
  }
</script>
<!--
<setup>
  import { defineComponent, ref } from 'vue'

  export default defineComponent({
    setup() {
      return {
        radio: ref('selected and disabled'),
      }
    }
  })
</setup>
-->
```

:::

### Radio button group

Suitable for choosing from some mutually exclusive options.

:::demo Combine `el-radio-group` with `el-radio` to display a radio group. Bind a variable with `v-model` of `el-radio-group` element and set label value in `el-radio`. It also provides `change` event with the current value as its parameter.

```html
<el-radio-group v-model="radio">
  <el-radio :label="3">Option A</el-radio>
  <el-radio :label="6">Option B</el-radio>
  <el-radio :label="9">Option C</el-radio>
</el-radio-group>

<script>
  export default {
    data() {
      return {
        radio: 3,
      }
    },
  }
</script>
<!--
<setup>
  import { defineComponent, ref } from 'vue'

  export default defineComponent({
    setup() {
      return {
        radio: ref(3),
      }
    }
  })
</setup>
-->
```

:::

### Button style

Radio with button styles.

:::demo You just need to change `el-radio` element into `el-radio-button` element. We also provide `size` attribute.

```html
<template>
  <div>
    <el-radio-group v-model="radio1">
      <el-radio-button label="New York"></el-radio-button>
      <el-radio-button label="Washington"></el-radio-button>
      <el-radio-button label="Los Angeles"></el-radio-button>
      <el-radio-button label="Chicago"></el-radio-button>
    </el-radio-group>
  </div>
  <div style="margin-top: 20px">
    <el-radio-group v-model="radio2" size="medium">
      <el-radio-button label="New York"></el-radio-button>
      <el-radio-button label="Washington"></el-radio-button>
      <el-radio-button label="Los Angeles"></el-radio-button>
      <el-radio-button label="Chicago"></el-radio-button>
    </el-radio-group>
  </div>
  <div style="margin-top: 20px">
    <el-radio-group v-model="radio3" size="small">
      <el-radio-button label="New York"></el-radio-button>
      <el-radio-button label="Washington" disabled></el-radio-button>
      <el-radio-button label="Los Angeles"></el-radio-button>
      <el-radio-button label="Chicago"></el-radio-button>
    </el-radio-group>
  </div>
  <div style="margin-top: 20px">
    <el-radio-group v-model="radio4" disabled size="mini">
      <el-radio-button label="New York"></el-radio-button>
      <el-radio-button label="Washington"></el-radio-button>
      <el-radio-button label="Los Angeles"></el-radio-button>
      <el-radio-button label="Chicago"></el-radio-button>
    </el-radio-group>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        radio1: 'New York',
        radio2: 'New York',
        radio3: 'New York',
        radio4: 'New York',
      }
    },
  }
</script>
<!--
<setup>
  import { defineComponent, ref } from 'vue'

  export default defineComponent({
    setup() {
      return {
        radio1: ref('New York'),
        radio2: ref('New York'),
        radio3: ref('New York'),
        radio4: ref('New York'),
      }
    }
  })
</setup>
-->
```

:::

### With borders

:::demo The `border` attribute adds a border to Radios.

```html
<template>
  <div>
    <el-radio v-model="radio1" label="1" border>Option A</el-radio>
    <el-radio v-model="radio1" label="2" border>Option B</el-radio>
  </div>
  <div style="margin-top: 20px">
    <el-radio v-model="radio2" label="1" border size="medium"
      >Option A</el-radio
    >
    <el-radio v-model="radio2" label="2" border size="medium"
      >Option B</el-radio
    >
  </div>
  <div style="margin-top: 20px">
    <el-radio-group v-model="radio3" size="small">
      <el-radio label="1" border>Option A</el-radio>
      <el-radio label="2" border disabled>Option B</el-radio>
    </el-radio-group>
  </div>
  <div style="margin-top: 20px">
    <el-radio-group v-model="radio4" size="mini" disabled>
      <el-radio label="1" border>Option A</el-radio>
      <el-radio label="2" border>Option B</el-radio>
    </el-radio-group>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        radio1: '1',
        radio2: '1',
        radio3: '1',
        radio4: '1',
      }
    },
  }
</script>
<!--
<setup>
  import { defineComponent, ref } from 'vue'

  export default defineComponent({
    setup() {
      return {
        radio1: ref('1'),
        radio2: ref('1'),
        radio3: ref('1'),
        radio4: ref('1'),
      }
    }
  })
</setup>
-->
```

:::

### Radio Attributes

| Attribute             | Description                          | Type                      | Accepted Values       | Default |
| --------------------- | ------------------------------------ | ------------------------- | --------------------- | ------- |
| model-value / v-model | binding value                        | string / number / boolean | —                     | —       |
| label                 | the value of Radio                   | string / number / boolean | —                     | —       |
| disabled              | whether Radio is disabled            | boolean                   | —                     | false   |
| border                | whether to add a border around Radio | boolean                   | —                     | false   |
| size                  | size of the Radio                    | string                    | medium / small / mini | —       |
| name                  | native 'name' attribute              | string                    | —                     | —       |

### Radio Events

| Event Name | Description                           | Parameters                          |
| ---------- | ------------------------------------- | ----------------------------------- |
| change     | triggers when the bound value changes | the label value of the chosen radio |

### Radio-group Attributes

| Attribute             | Description                                       | Type                      | Accepted Values       | Default |
| --------------------- | ------------------------------------------------- | ------------------------- | --------------------- | ------- |
| model-value / v-model | binding value                                     | string / number / boolean | —                     | —       |
| size                  | the size of radio                                 | string                    | medium / small / mini | —       |
| disabled              | whether the nesting radios are disabled           | boolean                   | —                     | false   |
| text-color            | font color when button is active                  | string                    | —                     | #ffffff |
| fill                  | border and background color when button is active | string                    | —                     | #409EFF |

### Radio-group Events

| Event Name | Description                           | Parameters                          |
| ---------- | ------------------------------------- | ----------------------------------- |
| change     | triggers when the bound value changes | the label value of the chosen radio |

### Radio-button Attributes

| Attribute | Description               | Type            | Accepted Values | Default |
| --------- | ------------------------- | --------------- | --------------- | ------- |
| label     | the value of radio        | string / number | —               | —       |
| disabled  | whether radio is disabled | boolean         | —               | false   |
| name      | native 'name' attribute   | string          | —               | —       |
