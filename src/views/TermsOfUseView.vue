<template>
    <header id="">
        <navBar />
    </header>

    <section>
        <termsOfUse />
    </section>

    <footer id="contacts">
        <footerContacts />
    </footer>
</template>
  
<script setup>

import navBar from '@/components/structure/navBar.vue';
import termsOfUse from '@/components/sections/TermsOfUseSections/termsOfUseSection.vue';
import footerContacts from '@/components/structure/footerContacts.vue';

</script>