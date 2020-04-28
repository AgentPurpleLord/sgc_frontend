<template>
    <div id="navigation" class="nav">
        <ul>
            <li>
                <a class="hvr-underline-from-center" :href="baseURL">Home</a>
            </li>
            <li>
                <a class="hvr-underline-from-center" href="#">Info</a>
            </li>
            <li class="nav__icon">
                <img :src="SGCIcon" />
            </li>
            <li>
                <a class="hvr-underline-from-center" href="#">Blog</a>
            </li>
            <li>
                <a target="_blank" class="hvr-underline-from-center" href="https://discord.gg/cmKbWsm">Discord</a>
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
            baseURL: process.env.VUE_APP_URL,
            SGCIcon: require('@/assets/svg/SGC-Icon.svg'),
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
    .nav ul, li, h1 {
        margin: 0px;
        padding: 0px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .nav__icon {
        padding: 10px;
    }

    .nav a {
        color: var(--yellow-01);
        text-decoration: none;
        padding: 8px 20px;
        font-size: 1.5rem;
        font-weight: 900;
        font-style: italic;
        text-transform: uppercase;
        transition: all 250ms ease-out;
    }

    .nav a:hover {
        font-size: 1.7rem;
        color: var(--orange-01);
    }

    .nav {
        text-align: center;
        list-style: none;
        color: var(--cyan-01);
        background: var(--black-01);
        border-bottom: 3px double var(--cyan-01);
    }

    .nav::before {
        content: " ";
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        background: linear-gradient(rgba(18, 16, 16, 0) 75%, rgba(0, 0, 0, 0.25) 75%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
        z-index: 2;
        background-size: 100% 2px, 3px 100%;
        pointer-events: none;
    }

    .nav__icon img {
        width: 100px;
        height: 100px;
    }
</style>