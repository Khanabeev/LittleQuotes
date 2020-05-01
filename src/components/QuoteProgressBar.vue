<template>
    <v-container>
        <v-row class="d-flex justify-center">
            <v-col cols="12">
                <v-progress-linear
                        :color="isMaximum ? 'red' : 'primary'"
                        value="100"
                        height="40px"
                        v-model="progressBar"
                >
                    <span style="color: white; font-size: 18px;">
                        {{ quotesQnt }} / {{ maxQuotes }}
                    </span>
                </v-progress-linear>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    export default {
        name: "QuoteProgressBar",
        props: {
            maxQuotes: {
                require: true,
                type: Number
            },
            quotesQnt: {
                require: true,
                type: Number
            },
            isMaximum: {
                type: Boolean,
                require: true
            }
        },
        computed: {
            progressBar: function () {
                return this.quotesQnt * 10
            },
        },
    }
</script>

<style scoped>

</style>