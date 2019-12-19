<script>

import RequestLink from './RequestLink'

export default {
    name: 'RequestGroup',
    components: {
        RequestLink
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
            <request-group v-if="resources.children" :routes="resources.children" class="ml-3"/>
            <ul class="ml-4" v-if="resources.routes">
                <li class="sm:mb-2" v-for="request in resources.routes" :key="request.id">
                    <request-link :request="request"/>
                </li>
            </ul>
        </details>
    </div>
</template>
