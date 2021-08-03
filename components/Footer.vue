<template>
    <section class="w-screen bg-blue-50 flex justify-between p-7 h-40">
        <div class="flex">
            <img src="../static/icon-48x48-2.png" alt="">
            <div class="flex items-center ml-5">
            <div class="text-2xl font-medium font-serif">Ko-rin Yamada</div>
            </div>
        </div>
        <div class="footer-menu flex space-x-6 items-center">
            <nuxt-link to='/' class='text-xl font-medium'>TOP</nuxt-link>
            <nuxt-link to='/profile' class='text-xl font-medium'>PROFILE</nuxt-link>
            <nuxt-link to='/works' class='text-xl font-medium'>WORKS</nuxt-link>
            <nuxt-link to='/blog' class='text-xl font-medium'>BLOG</nuxt-link>
            <nuxt-link to='/contact' class='text-xl font-medium'>CONTACT</nuxt-link>
        </div>
    </section>
</template>

<script>
export default {
    
}
</script>