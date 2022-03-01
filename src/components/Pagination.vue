<template>
    <ul class="pagination">
        <li 
            v-for="page in pages"
            :key="page"    
            class="page-item"
            :class="{ active: currentPage === page }"
        >
            <router-link 
            :to="{path: url, query: {page: page}}" 
            class="page-link"
            >
                {{ page }}
            </router-link>
        </li>
    </ul>
</template>

<script>
import {range} from '@/helpers/utils';

export default {
    name: 'McvPagination',
    props: {
        total: {
            type: Number,
            requered: true
        },
        limit: {
            type: Number,
            requered: true
        },
        currentPage: {
            type: Number,
            requered: true
        },
        url: {
            type: String,
            requered: true
        },
    },
    computed: {
        pages() {
            const pagesCount = Math.ceil(this.total / this.limit);
            return range(1, pagesCount);
        }
    }
}
</script>