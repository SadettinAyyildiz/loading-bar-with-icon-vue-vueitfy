<template>
    <v-dialog v-model="dialog" width="476">
        <v-card class="pa-8">
            <v-card-body class="pa-0 text-body-2" flat tile>
                <h3 class="mb-4 text-h6 black--text"> {{ from }} - {{ to }} uçuşları aranıyor… </h3>
                <p class="text-body-2">
                    <span>{{ dateOf }} - {{ dateTo }} |</span>
                    <span v-if="adultPassengers">{{ adultPassengers }} Yetişkin</span>
                    <span v-if="childPassengers">, {{ childPassengers }} Çocuk</span>
                </p>
            </v-card-body>

            <loading-bar-icon class="mt-11" :speed="25" />

        </v-card>

    </v-dialog>
</template>

<script>
import LoadingBarIcon from "@/components/common/dialogs/LoadingBarIcon";

export default {
    name: "LoadingDialog",
    components: {
        LoadingBarIcon
    },
    props:{
        speed:{
            default: 100
        },
        icon:{
            type: String,
            default: null
        },
        from:{
            //required: true,
            type: String,
            default: 'Kalkış'
        },
        to:{
            //required: true,
            type: String,
            default: 'Varış'
        },
        dateOf:{
            //required: true,
            default: 'Tarihinden'
        },
        dateTo:{
            //required: true,
            default: 'Tarihine'
        },
        adultPassengers:{
            //required: true,
            default: 1,
            type: Number
        },
        childPassengers: {
            type: Number
        }
    },
    data() {
        return {
            flightLinearLoading: 0,
            dialog: true
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
