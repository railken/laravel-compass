<script>

import HttpMethods from './HttpMethods'

export default {
    name: 'RouteGroup',
    components: {
        HttpMethods
    },
    props: ['routes'],
    methods: {
        toArray(obj) {
            return obj ? Object.values(obj) : []
        }
    }

}
</script>

<template>
    <div>
        <details class="sm:mb-2 cursor-pointer" v-for="(resources, name) in routes" :key="name">
            <summary class="px-2 -mx-2 py-1 hover:text-orange-600 focus:text-orange-600 text-gray-600 font-medium capitalize">
                {{name}}
            </summary>
            <route-group v-if="resources.children" :routes="resources.children" class="ml-3"/>
            <ul class="ml-4" v-if="resources.routes">
                <li class="sm:mb-2" v-for="request in resources.routes" :key="request.id">
                    <router-link :to="{name:'request', params:{id: request.id}}" active-class="text-orange-600" class="text-md px-2 -mx-2 py-1 hover:text-orange-600 text-gray-600">
                        <http-methods :request="request" />
                        <span class="ml-2">{{truncateString(request.title, 20)}}</span>
                    </router-link>
                </li>
            </ul>
        </details>
    </div>
</template>
