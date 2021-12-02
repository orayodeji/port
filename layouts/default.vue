<template>
    <div class="o-scroll" data-module-scroll="main">
        <div class="main-bg"></div>
        <main class="page-container">
            <TheNavbar />
            <div class="page js-locomote">
                <Nuxt />
            </div>
            <TCursor />
        </main>
    </div>
</template>

<script>
import LocomotiveScroll from 'locomotive-scroll';
import Cursor from '../js/cursor';

export default {
  mounted() {
    const locomote = document.querySelector(".js-locomote")
  
    window.addEventListener("load", () => {
        var scroll = new LocomotiveScroll({
            el: locomote,
            smooth: true
        });
    })

    // initialize custom cursor
    const cursor = new Cursor(document.querySelector('.cursor'));
  }
}
</script>