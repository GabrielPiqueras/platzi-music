<template lang="pug">
    section.hero.is-success
        .hero-head
            header.nav
                .container
                    .nav-left
                        .nav-item
                            strong Info Series
                            
                    //- Menu
                    nav.navbar(role='navigation' aria-label='main navigation') 
                        .navbar-brand
                            a.navbar-burger(v-bind:class="{ 'is-active': menuHamburguesa }", @click="mostrarMenuHamburguesa" role='button' aria-label='menu' aria-expanded='false' data-target='navbarBasicExample')
                                span(aria-hidden='true')
                                span(aria-hidden='true')
                                span(aria-hidden='true')
                        #navbarBasicExample.navbar-menu
                            .navbar-end

                            //- Idiomas
                            router-link.navbar-item(to="/") {{ $t('search') }}
                            router-link.navbar-item(to="about") {{ $t('about') }}
                            router-link.navbar-item(to="login") {{ $t('login') }}
                            router-link.navbar-item(to="registro") {{ $t('register') }}

                            .select
                                select(ref="idioma" @change="selectLang()")
                                    option(value='en' selected) English
                                    option(value='es') Spanish
        //- Portada (Hero)
        .hero-body
            .container.has-text-centered
                h1.title Info Series
                h2.subtitle {{ $t('description') }}
                //- Reproductor
                pm-player
 
</template>

<script>

import PmPlayer from '@/components/Player.vue'

export default {
    data() {
        return {
            menuHamburguesa: false
        }
    },
    components: {
        PmPlayer
    },
    methods: {
        mostrarMenuHamburguesa() {
            if (this.menuHamburguesa) {
                this.menuHamburguesa = false;
            } else {
                this.menuHamburguesa = true;
            }
        },
        selectLang() {
            let idioma = this.$refs.idioma.value
            this.$i18n.locale = idioma

            // Coloco el foco
            this.$refs.buscador.focus()
        }
    }
}
</script>