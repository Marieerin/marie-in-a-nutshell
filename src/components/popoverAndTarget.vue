<template>
    <span>
        <b-link :href="link" :id="targetName">
            React.js,
        </b-link> 
        <b-popover :target="targetName" triggers="hover" placement="top">
          <img src="../assets/fomTree.png" />
        </b-popover>
    </span>
</template>
<script> 
    export default {
        props:['targetName', 'link']
    }
</script>
