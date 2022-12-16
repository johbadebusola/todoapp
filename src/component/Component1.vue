<script>
export default {
   props: ["itemstodo","itemsStatus","isToggle"]

}

</script>
<template>

<div>
 
   <h4 v-if="(itemsStatus)" :class="{toggleH1:isToggle}">
      <ul   >
        <li  >
            {{ itemstodo }}
        </li>
      </ul>
    </h4>
    
</div>
</template>

