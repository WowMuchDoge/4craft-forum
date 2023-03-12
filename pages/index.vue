<script setup>
    const supabase = useSupabaseClient()
    const user = useSupabaseUser()

    const showMenu = ref(false)

    
</script>

<template>
<nav class="min-w-full h-14 max-lg:sticky bg-zinc-900 top-0 fixed z-20">
        <header class="justify-between flex">
        <div class="flex items-center w-10 max-lg:py-3.5"><a href="/" class="ml-10 text-xl font-semibold text-slate-200">4Craft</a></div>
        <div class="w-1/2 h-14 fixed flex translate-x-7o8 justify-end items-center top-0 lg:hidden max-lg"  @click="showMenu = !showMenu">
            <ul class="py-2 cursor-pointer" :class="{ 'change': 'isChanged' }">
                <div class="bar1 bg-slate-50 w-[35px] h-[5px] my-[6px] justify-end duration-500 bar1"></div>
                <div class="bar2 bg-slate-50 w-[35px] h-[5px] my-[6px] justify-end duration-500 bar2"></div>
                <div class="bar3 bg-slate-50 w-[35px] h-[5px] my-[6px] justify-end duration-500 bar3"></div>
            </ul> 
        </div>
        <div class="flex px-14 justify-end h-auto py-4 max-lg:hidden mont">
            <ul v-if="!user" class="px-10 transition duration-300 hover:-translate-y-0.5">
                <li><a href="/signup" class="text-slate-200 text-base font-normal transition duration-500 hover:opacity-60 ease-in-out">Sign Up</a></li>
            </ul>
            <ul v-if="!user" class="px-10 transition duration-300 hover:-translate-y-0.5">
                <li><a href="/login" class="text-slate-200 text-base font-normal transition duration-500 hover:opacity-60 ease-in-out">Log In</a></li>
            </ul>
            <ul v-if="user" class="px-10 transition duration-300 hover:-translate-y-0.5">
                <li><a href="/create-post" class="text-slate-200 text-base font-normal transition duration-500 hover:opacity-60 ease-in-out">Create Post</a></li>
            </ul>
            <ul class="px-10 transition duration-300 hover:-translate-y-0.5">
                <li><a href="#" class="text-slate-200 text-base font-normal transition duration-500 hover:opacity-60 ease-in-out">Posts</a></li>
            </ul>
            <ul class="px-10 transition duration-300 hover:-translate-y-0.5">
                <li><a href="#" class="text-slate-200 text-base font-normal transition duration-500 hover:opacity-60 ease-in-out">Users</a></li>
            </ul>
            <ul v-if="user" class="px-10 transition duration-300 hover:-translate-y-0.5">
                <li><a href="/Settings" class="text-slate-200 text-base font-normal transition duration-500 hover:opacity-60 ease-in-out">User Settings</a></li>
            </ul>
            <ul class="px-10 transition duration-300 hover:-translate-y-0.5">
                <li><a href="#" class="text-slate-200 text-base font-normal transition duration-500 hover:opacity-60 ease-in-out">Search</a></li>
            </ul>
        </div>
    </header>
    </nav>

    <div v-if="showMenu" class="fixed flex w-1/2 items-center justify-end z-50" id="mendiv">
        <div class="w-full h-screen flex justify-start translate-x-full z-50 duration-500 menu -translate-y-1 bg-zinc-900 slide" id="menu">
            <ul class="px-14 text-xl py-4 text-slate-200 max-[382px]:text-lg">
                <a href="/signup" v-if="!user"><li class="py-2"><h1>Sign Up</h1></li></a>
                <a href="/login" v-if="!user"><li class="py-2"><h1>Log In</h1></li></a>
                <a href="/create-post" v-if="user"><li class="py-2"><h1>Create Post</h1></li></a>
                <a href="/settings"><li class="py-2"><h1>Posts</h1></li></a>
                <a href="/settings"><li class="py-2"><h1>Users</h1></li></a>
                <a href="/settings"><li v-if="user" class="py-2"><h1>User Settings</h1></li></a>
                <a href="/settings"><li v-if="user" class="py-2"><h1>Search</h1></li></a>
            </ul>
        </div>
    </div>

    <div class="w-screen h-screen bg-zinc-800 absolute flex justify-center items-center">
    </div>

    <div class="w-screen h-screen bg-black z-40"></div>

</template>

<style scoped>
    @import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Open+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,300;1,400;1,500;1,600;1,700;1,800&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
    
    .poppins {
        font-family: 'Poppins', sans-serif;
    }

    .mont {
        font-family: 'Montserrat', sans-serif;
    }

    .open-sans {
        font-family: 'Open Sans', sans-serif;
    }

    .translate-x-7o8 {
        transform: translateX(87.5%);
    }

    .slide-enter-active,
    .slide-leave-active {
    transition: transform 0.5s ease-in-out;
    }

    .slide-enter,
    .slide-leave-to {
        transform: translateX(100%);
    }

    .isChanged .bar1 {
        transform: translate(0, 11px) rotate(-45deg);
    }

    .isChanged .bar2 {opacity: 0;}

    .isChanged .bar3 {
        transform: translate(0, -11px) rotate(45deg);
    }
</style>