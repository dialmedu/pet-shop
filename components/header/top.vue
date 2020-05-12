<template>
    <section class="top">
            <div class="left">
                <ul>
                    <li v-for="(menu, i) in menus" v-bind:key="i">
                        <a :href="menu.href">{{menu.title}}</a>
                    </li>
                </ul>
            </div>
            <div class="center">
                <p class="text-offer">
                    <b class="color-primary">30% Sale</b>
                    <span >of your first <li><font-awesome-icon icon="box-open" class="icon color-primary" fixed-width /></li></span>
                    <b>Autoship</b>
                </p>
            </div>
            <div class="right">
                <div class="auth">
                    <div v-if="true">
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
                    <a href="/cart">
                        <div class="box-icon">
                            <font-awesome-icon icon="shopping-cart" class="icon" fixed-width ></font-awesome-icon>
                        </div>
                        <span class="margin-r5">Cart</span>
                        <span>(10)</span>
                    </a>
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
    section>.left>ul{
        display: flex;
        padding-left: 0;
    }

    section>.left>ul>li{
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
        background-color: var(--primary-color);
        height: 100%;
        padding: 15px 8px;
        cursor: pointer;
        display: flex;
    }

    section .box-shopping-cart>a{
        display: flex;
    }

    section .box-shopping-cart>a>div{
        height: 17px;
        width: 17px;
        margin-right: 8px;
        overflow: hidden;
        position: relative;
        top: 1.9px;
    }
        
    section .box-shopping-cart>a>div>.icon{
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
</style>