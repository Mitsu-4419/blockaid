<template>
    <span class="badge hover:bg-gray-300 hover:text-gray-400">{{tag}}</span>
</template>

<script>
export default {
    props:{
        tag:{
            type:String,
            default:''
        }
    }
}
</script>

<style>
.badge {
  @apply bg-indigo-900 text-gray-100 text-xs uppercase font-bold rounded-full p-2 absolute top-0 left-2 mt-2 ;
}
</style>