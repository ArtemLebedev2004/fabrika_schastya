<template>
    <header id="">
        <navBar />
    </header>

    <section>
        <userAgreement />
    </section>

    <footer id="contacts">
        <footerContacts />
    </footer>
</template>
  
<script setup>

import navBar from '@/components/structure/navBar.vue';
import userAgreement from '@/components/sections/UserAgreementSections/userAgreementSection.vue';
import footerContacts from '@/components/structure/footerContacts.vue';

</script>

