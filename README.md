# vue-placeholder-loader

## Usage
```vue
<template>
  <crm-loader :isLoading="isLoading" :rows="10" :column="1" template="bulletList">
    <!-- Content to be Displayed-->
  </crm-loader>
</template>
<script>
import CrmLoader from './crmLoader/crmLoader';

export default {
  components: {
    CrmLoader
  },
  data() {
    return {
      isLoading: false,
    }
  }
}
</script>
```

## API
### Props
|Prop|Type|Default|Description|
|---|---|---|---|
|isLoading|Boolean|false|This is for the conditional visibility of loader and its corresponding content|
|template|String|list|list,bulletList,tableList,box,imgBodyHorizontal,imgBodyVertical|
|row|Number|5|Number of lines to be displayed|
|column|Number|1|Number of columns to be displayed|
|field|Array|[]|This is only applicable for tableList template|

## Notes
This is only a vue component not a vue plugin. This also uses bootstrap-vue for its layout.
