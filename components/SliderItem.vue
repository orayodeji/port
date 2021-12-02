<template>
    <div class="portfolio__random--images">
        <div class="portfolio__random--images-image__item" :class="[active ? 'active' : '']"
          :data-active="[active ? 'active' : '']"
        >
          <img :src="image" alt="" srcset="" />
        </div>

        <div class="portfolio__random--images-image__item" :class="[active ? 'active' : '']">
            <img :src="image" alt="" class="bg" />
        </div>
    </div>
</template>

<script>
export default {
    props: {
        image: String,
        active: Boolean
    },
}
</script>