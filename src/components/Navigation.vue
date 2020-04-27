<template>
    <div id="navigation" class="nav">
        <ul v-for="item in navpages" :key="item.id">
            <li>
                <a :href="item.html_url">{{ item.title }}</a>
            </li>           
        </ul>
    </div>
</template>

<script>
import axios from '@/axios'

export default {
    name: 'Navigation',
    data () {
        return {
            navpages: {}
        }
    },
    mounted () {
        axios
            .get('pages/?&show_in_menus=true')
            .then(response => (this.navpages = response.data.items))
    }
}
</script>

<style>
    .nav li, h1 {
        display: inline;
        vertical-align: middle;
    }

    .nav__icon {
        padding: 10px;
    }

    .nav a {
        padding: 8px;
    }

    .nav {
        text-align: center;
        list-style: none;
        color: var(--cyan-01);
    }
</style>