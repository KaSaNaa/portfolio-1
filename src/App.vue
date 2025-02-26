<template>
    <div id="app" :class="this.$route.meta.bodyClass">
        <Spinner></Spinner>
        <BgBody />

        <Header :routeName="this.$route.name" :viewport="viewport" />

        <transition
            appear
            mode="out-in"
            :css="false"
            @leave="leave"
            @enter="enter"
        >
            <router-view :viewport="viewport" />
        </transition>

        <Spine />
    </div>
</template>

<script setup>
// styles
import '@/styles/app.scss'
import '@/styles/nprogress.scss'
// GSAP + ScrollMagic
import * as ScrollMagic from 'scrollmagic'
import { TweenMax, TimelineMax } from 'gsap'
import { ScrollMagicPluginGsap } from 'scrollmagic-plugin-gsap'
ScrollMagicPluginGsap(ScrollMagic, TweenMax, TimelineMax)
// Components
import Header from '@/components/Header.vue'
import Spine from '@/components/Spine.vue'
import BgBody from '@/components/BgBody.vue'
import Spinner from './components/Spinner.vue'

const viewport = reactive({
    w: window.innerWidth,
    h: window.innerHeight,
    is568: window.innerWidth <= 568,
    is768: window.innerWidth <= 768,
    is1024: window.innerWidth <= 1024,
})

const introTimeline = new TimelineMax()
const leaveTimeline = new TimelineMax()

onMounted(() => {
    // update viewport
    updateViewport()
    // add resize listener
    window.addEventListener('resize', updateViewport)
    // add beforeunload listener, in case of refresh
    window.addEventListener('beforeunload', () => window.scroll(0, 0))
})

function enter(el, done) {
    // intro animations
    introTimeline
        .clear()
        .addLabel('enter', 0)
        .fromTo(
            '.header-breadcrumb',
            1,
            {
                autoAlpha: 0,
                x: -32,
            },
            {
                autoAlpha: 1,
                x: 0,
                ease: Power3.easeOut,
            },
            'enter'
        )
        .fromTo(
            el,
            1,
            {
                autoAlpha: 0,
            },
            {
                autoAlpha: 1,
            },
            'enter'
        )
        .fromTo(
            '.spine',
            1,
            {
                autoAlpha: 0,
                yPercent: 20,
            },
            {
                autoAlpha: 1,
                yPercent: 0,
                ease: Power3.easeOut,
                onComplete: done,
            },
            'enter'
        )
        .fromTo(
            '.spine-target .circle',
            1,
            {
                scale: 0,
                autoAlpha: 0,
            },
            {
                scale: 1,
                autoAlpha: 1,
                ease: Elastic.easeOut.config(1, 0.5),
            },
            'enter+=.7'
        )
        .fromTo(
            '.spine-target .circle',
            2,
            {
                backgroundColor: 'transparent',
            },
            {
                backgroundColor: '#ff0000',
            },
            'enter+=1.2'
        )
        .fromTo(
            '.spine-target .pulse',
            4,
            {
                autoAlpha: 1,
                scale: 0,
            },
            {
                autoAlpha: 0,
                scale: 8,
                ease: Power3.easeOut,
            },
            'enter+=1.2'
        )
}

function leave(el, done) {
    // leave animations
    leaveTimeline
        .clear()
        .addLabel('leave', 0)
        .to(
            '.spine-target .circle, .spine-target .pulse',
            0.5,
            {
                scale: 0,
                autoAlpha: 0,
                ease: Power3.easeIn,
            },
            'leave'
        )
        .to(
            '.spine',
            0.5,
            {
                autoAlpha: 0,
                yPercent: 50,
                ease: Power3.easeIn,
            },
            'leave+=.25'
        )
        .set('.header-breadcrumb', { autoAlpha: 0 }, 'leave')
        .to(
            el,
            1,
            {
                autoAlpha: 0,
                onComplete: done,
            },
            'leave'
        )
}

function updateViewport() {
    // update
    viewport.w = window.innerWidth
    viewport.h = window.innerHeight
    viewport.is568 = window.innerWidth <= 568
    viewport.is768 = window.innerWidth <= 768
    viewport.is1024 = window.innerWidth <= 1024
}
</script>
