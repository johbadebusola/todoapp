<script>
export default {
   props: ["itemstodo","itemsStatus"],
   inheritAttrs: false
}
</script>
<template>

<div>
 
   <h4 v-if="(itemsStatus)">
      <ul>
        <li  v-bind="$attrs">
            {{ itemstodo }}
        </li>
      </ul>
    </h4>
    
</div>
</template>