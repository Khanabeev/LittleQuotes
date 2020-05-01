<template>
    <v-container>
        <v-row>
            <v-col lg="3" md="4" sm="6" v-for="(quote, index) in quotes" :key="index">
                <div @click="deleteQuote(index)">
                    <quote>
                        <h3 slot="title">Quote ID: {{ quote.id }}</h3>
                        <p slot="text">{{ quote.text }}</p>
                    </quote>
                </div>

            </v-col>
        </v-row>

    </v-container>
</template>

<script>
    import Quote from "@/components/Quote";
    export default {
        name: "QuoteGrid",
        components: {Quote},
        props: {
            quotes: {
                type: Array,
                require: true
            }
        },
        methods: {
            deleteQuote: function (index) {
                console.log(index + " Grid")
                this.$emit('deleteOneQuote', index);
            }
        }
    }
</script>

<style scoped>
    h3{
        font-size: 16px;
        font-style: italic;
    }
</style>