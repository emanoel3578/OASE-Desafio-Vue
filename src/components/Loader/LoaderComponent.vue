<template>
    <div class="flex h-screen justify-center items-center">
    <svg fill='none' class="w-16 h-16 animate-spin" viewBox="0 0 32 32" xmlns='http://www.w3.org/2000/svg'>
        <path class="text-purple-400" clip-rule='evenodd'
        d='M15.165 8.53a.5.5 0 01-.404.58A7 7 0 1023 16a.5.5 0 011 0 8 8 0 11-9.416-7.874.5.5 0 01.58.404z'
        fill='currentColor' fill-rule='evenodd' />
    </svg>
    <div class="text-purple-400 text-2xl">
        <h1>
        O App está carregando
        </h1>
    </div>
    </div>
</template>

<script>
export default {
    name:'Loader',
}

</script>