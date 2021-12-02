<template>
    <div class="portfolio__theme--wrapper">
        <span class="theme__palette--text">Color Palette: </span>
        <button type="button" @click="setTheme('light-mode')" class="color__pallete--button color__pallete--button__FFFFFF-mode" inert>
            <span class="color__pallete--button__inner">Color 1</span>
        </button>
        <button type="button" @click="setTheme('__88D498-mode')" class="color__pallete--button color__pallete--button__88D498-mode">
            <span class="color__pallete--button__inner">Color 88D498</span>
        </button>
        <button type="button" @click="setTheme('__CCD6F6-mode')" class="color__pallete--button color__pallete--button__CCD6F6-mode">
            <span class="color__pallete--button__inner">Color CCD6F6</span>
        </button>
    </div>
</template>

<script>
export default {
    methods: {
        setTheme(theme) {
            document.documentElement.className = theme;
        }
    }
}
</script>

<style scoped>
.color__pallete--button {
    position: relative;
    width: 15px;
    height: 27.5px;
    margin-top: 12.5px;
    padding-top: 12.5px;
}

@media only screen and (min-width: 800px) {
    .portfolio__theme--wrapper {
        padding: 0px;
        margin: 0px;
        position: fixed;
        width: 210px;
        z-index: 90;
        transform: rotate(-90deg);
    }

    .portfolio__theme--wrapper {
        right: -100px;
        top: 230px;
        left: auto;
        bottom: auto;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -ms-flex-wrap: nowrap;
        flex-wrap: nowrap;
        -webkit-box-pack: end;
        -ms-flex-pack: end;
        justify-content: flex-end;
        -webkit-box-align: start;
        -ms-flex-align: start;
        align-items: flex-start;
    }

    .portfolio__theme--wrapper .theme__palette--text {
        -webkit-transition: color .4s linear;
        transition: color .4s linear;
        position: relative;
        font-weight: 500;
        font-style: italic;
        display: block;
        top: -.16em;
        font-size: 12px;
        letter-spacing: .015em;
        text-transform: lowercase;
    }

    .color__pallete--button {
        width: 10px;
        height: 15px;
        padding-top: 0;
        margin-top: 0;
        margin-left: 6px;
    }
}

button {
    margin: 0;
    border-radius: 0;
    border: none;
    background-color: transparent;
    cursor: pointer;
    padding: 0;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    color: inherit;
    font-family: inherit;
    font-weight: inherit;
    font-size: inherit;
    display: block;
    text-align: left;
    -webkit-touch-callout: none;
    user-select: none;
    -webkit-user-select: none;
}

[inert], [inert] * {
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}

[inert] {
    pointer-events: none;
    cursor: default;
}

.light-mode .color__pallete--button__FFFFFF-mode .color__pallete--button__inner,
.__88D498-mode .color__pallete--button__88D498-mode .color__pallete--button__inner {
    -webkit-transform: scaleX(1);
    transform: scaleX(1);
}   

.color__pallete--button__FFFFFF-mode .color__pallete--button__inner {
    background-color: #FFFFFF;
}

.color__pallete--button__88D498-mode .color__pallete--button__inner {
    background-color: #88D498;
}

.color__pallete--button__CCD6F6-mode .color__pallete--button__inner {
    background-color: #CCD6F6;
}



.color__pallete--button__inner {
    text-indent: 120%;
    white-space: nowrap;
    overflow: hidden;
    line-height: .1;
    display: block;
    position: relative;
    width: 100%;
    height: 100%;
    -webkit-transform: scaleX(.5);
    transform: scaleX(.5);
    -webkit-transform-origin: center left;
    transform-origin: center left;
    background-color: #7d97b8;
    -webkit-transition-duration: transform .4s cubic-bezier(.19,1,.22,1);
    transition-duration: transform .4s cubic-bezier(.19,1,.22,1);
}

@media screen and (min-width: 800px) {
    .color__pallete--button__inner {
        -webkit-transform-origin: top center;
        transform-origin: top center;
        -webkit-transform: scaleY(.6667);
        transform: scaleY(.6667);
    }
}
</style>