<template>
    <section class="top">
            <div class="left">
                <nav>
                    <li v-for="(menu, i) in menus" v-bind:key="i">
                        <a :href="menu.href">{{menu.title}}</a>
                    </li>
                </nav>
            </div>
            <div class="center">
                <p class="text-offer">
                    <b class="color-blue">30% Sale</b>
                    <span >of your first <li><font-awesome-icon icon="box-open" class="icon color-blue" fixed-width /></li></span>
                    <b>Autoship</b>
                </p>
            </div>
            <div class="right">
                <div class="auth">
                    <div v-if="!auth">
                        Account
                    </div>
                    <div v-else>
                        <a href="#">Login</a>
                    </div>
                </div>
                <div class="box-icon-actions">
                    <li class="box-icon" v-for="(item, i) in sectionIcon" v-bind:key="i">
                        <font-awesome-icon :icon="[item.prefix, item.icon]" v-if="item.prefix"/>
                        <font-awesome-icon :icon="item.icon" v-else/>
                    </li>
                </div>
                <div class="box-shopping-cart">
                    <div class="box-icon">
                        <font-awesome-icon icon="shopping-cart" class="icon" fixed-width ></font-awesome-icon>
                    </div>
                    <span class="margin-r5">Cart</span>
                    <span>(10)</span>
                </div>
            </div>
        </section>
</template>

<script>
    import Vue from 'vue'
    import { library } from '@fortawesome/fontawesome-svg-core'
    import { faBoxOpen, faBell, faShoppingCart } from '@fortawesome/free-solid-svg-icons'
    import { faStar } from '@fortawesome/free-regular-svg-icons';
    import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

    library.add(faStar, faBoxOpen, faBell, faShoppingCart)
    
    Vue.component('font-awesome-icon', FontAwesomeIcon)

    export default Vue.extend({
        data() {
            return {
                menus: [
                    {title: "Contact us", href: "contact-us"},
                    {title: "About Us", href: "about-us"},
                    {title: "FAQ", href: "FAQ"},
                    {title: "Pet Health Blog", href: "blog"},
                ],
                sectionIcon: [
                    {prefix: "far", icon: "star"},
                    {icon: "bell"}
                ]
            }
        }
    })
</script>

<style scoped>

    section{
        background-color: #3f464f;
        padding: 0 20px;
        display: flex;
    }

    section>div{
        display: flex;
        align-items: center;
    }

    section>.center{
        flex: 1 1 auto;
        justify-content: center;
    }

    section>div:first-child,
    section>div:last-child{
        min-width: 370px;
        max-width: 370px;
    }

    /* LEFT */
    section>.left>nav{
        display: flex;
    }

    section>.left>nav>li{
        margin-right: 25px;
    }

    /* RIGHT */
    section>.right{
        justify-content: flex-end;
    }

    section .box-icon-actions{
        display: grid;
        padding: 0 15px;
        grid-gap: 15px;
        grid-template-columns: 1fr 1fr;
    }

    section .box-icon-actions>li{
        cursor: pointer;
    }

    section .box-shopping-cart{
        background-color: #66a7e9;
        height: 100%;
        padding: 15px 8px;
        cursor: pointer;
        display: flex;
    }

    section .box-shopping-cart>div{
        height: 17px;
        width: 17px;
        margin-right: 8px;
        overflow: hidden;
        position: relative;
        top: 1.9px;
    }
        
    section .box-shopping-cart>div>.icon{
        width: 100%;
        height: 100%;
    }

    section .box-shopping-cart .margin-r5{
       margin-right: 5px!important;
    }

    section .text-offer,
    section .text-offer span{
        display: flex;
    }

    section .text-offer span{
        margin: 0 8px;
    }

    section .text-offer span .icon{
        position: relative;
        margin-left: 8px;
        top: 1px;
    }

    .color-blue{
        color: #66a7e9;
    }
</style>