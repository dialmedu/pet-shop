<template>
    <section>
        <div class="box-icon">
            <img src="@/assets/logo.png" alt="">
        </div>
        <div class="box-info">
            <span>
                <font-awesome-icon icon="truck" class="color-primary"/>
            </span>
            <span>
                <a href="#">FAST FREE SHIPPING OVER $49</a>
            </span>
        </div>
        <div class="box-menu">
            <nav>
                <li v-for="(item, i) in menus" v-bind:key="i">
                    <span v-if="item.active" class="active">•</span>
                    <span>
                        <a :href="item.href || '#'">{{item.title}}</a>
                    </span>
                    <span v-if="item.submenu" class="arrow">
                        <font-awesome-icon icon="chevron-down" class="icon"/>
                    </span>
                </li>
            </nav>
        </div>
        <div class="box-search">
            <div class="content-search">
                <input type="text" placeholder="Search">
                <font-awesome-icon icon="search" class="icon"/>
            </div>
        </div>
    </section>
</template>

<script>
    import Vue from 'vue'

    import { library } from '@fortawesome/fontawesome-svg-core'
    import { faTruck, faSearch, faChevronDown } from '@fortawesome/free-solid-svg-icons'
    import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

    library.add(faTruck, faSearch, faChevronDown)
    
    Vue.component('font-awesome-icon', FontAwesomeIcon)

    export default Vue.extend({
        data() {
            return {
               menus: [
                   {title: "PET", submenu: [], active: true},
                   {title: "PHARMACY", submenu: []},
                   {title: "BRAND"},
                   {title: "SALE"},
                   {title: "PRESCRIPTION"},
               ]
            }
        },
        components: {

        }
    })
</script>

<style scoped>
    section{
        display: flex;
        align-items: center;
        padding: 10px 15px;
        max-height: 90px;
        height: 90px;
        overflow: hidden;
        box-sizing: border-box;
        color: black;
        border-bottom: 1px solid rgba(0,0,0,.02);
    }

    section li,
    section a,
    section span{
        color: black;
    }

    section>div{
        display: flex;
        align-items: center;
    }

    section .box-icon{
        width: 140px;
        height: 100%;
        cursor: pointer;
        margin-right: 40px;
    }

    section .box-icon>img{
        position: relative;
        height: 100%;
        width: 100%;
        object-fit: contain;
        top: -5px;
    }

    section .box-info>span:first-child{
        padding-right: 5px;
    }

    section .box-info>span:last-child{
        font-weight: 400;
        opacity: .8;
    }

    section .box-menu{
        flex:  1 1 auto;
        padding: 0 70px;
    }

    section .box-menu>nav{
        width: 100%;
        display: flex;
    }

    section .box-menu>nav>li{
       margin-right: 35px;
       font-weight: bold;
    }

    section .box-menu>nav>li:last-child{
        margin-right: 0;
    }

    section .box-menu>nav>li>.active,
    section .box-menu>nav>li>.arrow>.icon{
        color: var(--primary-color);
    }

    section .box-search>.content-search{
        border: 1px solid var(--primary-color);
        padding: 5px 15px 7px 15px;
        border-radius: 40px;
    }

    section .box-search>.content-search>input{
        border: none;
        height: 100%;
    }

    section .box-search>.content-search>input:focus{
        outline: none;
    }

    section .box-search>.content-search>input::-webkit-input-placeholder,
    section .box-search>.content-search>input:-ms-input-placeholder,
    section .box-search>.content-search>input::placeholder{
        color: rgba(0,0,0,.6);
        font-weight: bold;
    }

    section .box-search>.content-search .icon{
         color: rgba(0,0,0,.6);
    }

    
</style>