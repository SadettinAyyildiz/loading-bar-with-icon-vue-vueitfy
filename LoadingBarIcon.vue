<template>

    <v-card class="mb-3" flat tile>
        <v-progress-linear height="5" rounded v-model="flightLinearLoading" background-color="primary lighten-4">
            <template #default="{value}">
                <v-icon :style="`margin-left: ${value}%; position: absolute; left:0; margin-top: 2px`" color="primary" size="28">
                    {{icon}}
                </v-icon>
            </template>
        </v-progress-linear>
    </v-card>

</template>

<script>
export default {
    name: "LoadingBar",
    props:{
        speed:{
            default: 100
        },
        icon:{
            type: String,
            default: 'mdi-airplane mdi-rotate-90'
        },
    },
    data() {
        return {
            flightLinearLoading: 0
        }
    },
    mounted() {
        this.startLoading()
    },
    methods: {
        startLoading() {
            setInterval(() => {
                this.flightLinearLoading++
                if (this.flightLinearLoading === 100) {
                    this.flightLinearLoading = 0
                }
            }, this.speed)
        }
    }
}
</script>

<style lang="scss" scoped>
.v-progress-linear{
    overflow: visible !important;
    transition: 0s !important;

    .v-icon{
        transition: 0s !important;
    }
}
</style>
