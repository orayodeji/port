<template>
    <div data-scroll-container>
        <section class="portfolio__hero" data-scroll-section>
            <div class="container position-relative">
                <div class="animated__blob--wrapper">
                    <div class="animated__blob--ring"></div>
                    <ImageSlider :imagesData="imageData" />
                </div>
                <div class="row justify-content-start">
                    <div class="col-md-6">
                        <div class="portfolio__header">
                            <div class="portfolio__title">
                                <h1 data-scroll data-scroll-speed="2.5">Hi, I'm <br> Tuunji Ayodeji </h1>
                            </div>
                            <div class="portfolio__text">
                                <p data-scroll data-scroll-speed="2">
                                    I am a Front-End Engineer based in Lagos NG.
                                     <!-- &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -->
                                    I recently joined the engineering team at 
                                    <span class="current-employer">
                                        <a href="http://" target="_blank" rel="noopener noreferrer">Tishlabs</a>    
                                    </span>, where I work on a wide variety of interesting and meaningful projects on a daily basis.
                                </p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <HelpBusiness />
        <Projects />
        <About />
        <!-- <Companies /> -->
        <Ready />
        <TheFooter />
    </div>
</template>

<script>
import imageData from '../images'

export default {
    data() {
        return {
            imageData
        }
    },
    mounted() {
        console.log(this.imageData);
    }
}
</script>


<style scoped>

</style>