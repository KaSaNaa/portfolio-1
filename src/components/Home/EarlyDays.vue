<template>
    <div>
        <Titles :viewport="viewport" scene="earlyTitle">
            <h1 class="title" v-if="viewport.is568">
                Check out my socials<br />
                (<span class="params">stalk me</span>)
            </h1>
            <h1 class="title" v-else>
                Check out my socials (<span class="params">stalk me</span>)
            </h1>

            <div class="std">
                <p class="-gray">&lt;avin.here&gt;</p>
            </div>

            <div class="clouds cloud-1"></div>

            <div class="pepe bg-head">
                <div class=""></div>
                <div class=""></div>
                <div class=""></div>
                <div class="">
                    <div class=""></div>
                    <div class="">
                        <div class=""></div>
                        <div class=""></div>
                        <div class=""></div>
                        <div class=""></div>
                    </div>
                    <div class=""></div>

                    <div class=""></div>

                    <div class=""></div>
                    <div class=""></div>
                </div>
                <div class="am-pa">
                    <div class=""></div>
                    <div class=""></div>
                    <div class=""></div>
                    <div class=""></div>
                    <div class=""></div>
                    <div class=""></div>
                    <div class=""></div>
                    <div class=""></div>
                </div>
                <div class="metals">
                    <div class=""></div>
                    <div class=""></div>
                    <div class="">
                        <div class=""></div>
                    </div>
                </div>

                <div class=""></div>
                <div class=""></div>

                <div class=""></div>
            </div>

            <div class="clouds cloud-2"></div>
            <div class="clouds cloud-3"></div>

            <div class="pepe-scenery" role="img" aria-labelledby="pepeDesc">
                <p class="ariaLabel" id="pepeDesc">
                    A floating head carrying musical instruments in the ear,
                    foliage and monuments in the hair, flies over a greenish
                    ocean during the sunset
                </p>
                <div class="sky"></div>
                <div class="ocean">
                    <div class="sky-mask"></div>
                    <div class="ocean-waves w1"></div>
                    <div class="ocean-waves w2"></div>
                </div>
            </div>
        </Titles>

        <section class="scene" id="early-days">
            <div class="static-container">
                <div class="std">
                    <p>Find me around.</p>
                    <p class="-big">
                        Read my mind...<br />
                        <span class="-purple"
                            ><a
                                href="https://twitter.com/avinhere"
                                target="_blank"
                                title="Visit Biz Commerce's website"
                                >uhm, I mean my tweets!</a
                            ></span
                        >
                    </p>
                </div>
            </div>
        </section>
        <section class="scene" id="early-days2">
            <div class="static-container">
                <div class="std">
                    <p class="-big">
                        <span class="-purple">Check out </span>
                        <span class="-purple">some of my opensource,</span
                        ><br />
                        <span class="-purple">work on </span>
                        <span class="-purple"
                            ><a
                                href="https://github.com/avincodes"
                                target="_blank"
                                title="Visit Biz Commerce's website"
                                >Github!</a
                            ></span
                        >
                    </p>
                    <p>
                        <br />
                    </p>
                </div>
            </div>
        </section>
        <section class="scene" id="early-days3">
            <div class="static-container">
                <div class="std">
                    <p>
                        <br />

                        <span class="-big -purple"
                            ><i>Find </i> <i>my beats</i> on <i></i
                            ><a
                                href="https://open.spotify.com/user/6yurjrwd1ow722bilrg5vvn8z?si=dc3a6c4293ab4094"
                                target="_blank"
                                title="Visit Biz Commerce's website"
                                >"Spotify"</a
                            >.</span
                        >
                    </p>
                </div>
            </div>
        </section>
    </div>
</template>

<script setup>
import { reactive } from 'vue'
import Titles from './Titles.vue'

const viewport = reactive({
    w: window.innerWidth,
    h: window.innerHeight,
    is568: window.innerWidth <= 568,
    is768: window.innerWidth <= 768,
    is1024: window.innerWidth <= 1024,
})
</script>
