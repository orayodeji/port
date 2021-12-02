<template>
    <section class="pb-7 pb-lg-10" data-scroll-section>
        <div class="container position-relative">
            <div class="row justify-content-start mb-6 mb-lg-7">
                <div class="col-md-8">
                    <p class="header" data-scroll data-scroll-speed="2.5">About me</p>
                    <h1 class="title" data-scroll data-scroll-speed="1.5">
                        Get to know a little about me 
                    </h1>
                    <p class="portfolio__about--me" data-scroll data-scroll-speed="2.0">
                        Hi! I’m Samuel, an experienced front-end developer based in Lagos, Nigeria.
                        I enjoy creating websites, applications, or anything in between. My goal is to build products that provide pixel-perfect, performant experiences.
                                            
                        Here are a few technologies I've been working with recently in order of expertise:
                    </p>
                    <ul class="w-80 check__list portfolio__check--column mt-3" data-scroll data-scroll-speed="1.5">
                        <li class="check__list--item">
                            HTML
                        </li>
                        <li class="check__list--item">
                            CSS
                        </li>
                        <li class="check__list--item">
                            Node
                        </li>
                        <li class="check__list--item">
                            Express                            
                        </li>
                        <li class="check__list--item">
                            JavaScript (ES5 + ES6)
                        </li>
                        <li class="check__list--item">
                            Vue JS
                        </li>
                        <li class="check__list--item">
                            Nuxt JS
                        </li>
                        <li class="check__list--item">
                            Optimization Techniques
                        </li>
                        <li class="check__list--item">
                            Agile Development
                        </li>
                    </ul>
                </div>
            </div>
            <div class="animated__blob--wrapper portfolio__about--blob">
                <div class="animated__blob--ring"></div>
                <div class="imageSlider">
                    <div class="portfolio__random--images">
                        <div class="portfolio__random--images-image__item active my-face">
                            <img src="~/assets/imgs/face.jpeg" alt="It's My Real Face" srcset="" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import imageData from '../images'

export default {
    data() {
        return {
            imageData
        }
    },  
}
</script>

<style scoped>

</style>