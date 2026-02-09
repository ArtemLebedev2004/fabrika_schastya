<template>
    <header id="">
        <navBar />
    </header>

    <section>
        <termsOfCookie />
    </section>

    <footer id="contacts">
        <footerContacts />
    </footer>
</template>
  
<script setup>

import navBar from '@/components/structure/navBar.vue';
import termsOfCookie from '@/components/sections/TermsOfCookieSections/termsOfCookieSection.vue';
import footerContacts from '@/components/structure/footerContacts.vue';

</script>