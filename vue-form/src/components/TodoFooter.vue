<template>
    <div class="clearAllContainer">
        <button type="clearAllBtn" v-on:click="clearAll">Clear All</button>
    </div>
</template>

<script>
export default {
    methods: {
      clearAll(){
        this.$emit('clearOne');
      }
        }
}
</script>
<style scoped>
.clearAllContainer {
    width: 8.5rem;
    height: 50px;
    line-height: 50px;
    background-color: white;
    border-radius: 5px;
    margin: 0 auto;
}

.clearAllBtn {
    color: #e20303;
    display: block;
}
</style>