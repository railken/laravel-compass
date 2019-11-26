<script>

import HttpMethods from './HttpMethods'

export default {
    props: ['request'],
    components: {
        HttpMethods
    }

}
</script>

<template>
    <router-link :to="{name:'request', params:{id: request.id}}" active-class="text-orange-600" class="text-md px-2 -mx-2 py-1 hover:text-orange-600 text-gray-600 truncate">
        <http-methods :request="request" />
        <span class="ml-2">{{truncateString(request.title, 20)}}</span>
    </router-link>
</template>

<style scoped>
    .one-line {

    }
</style>