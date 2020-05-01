<template>
    <v-container>
        <v-row>
            <v-col>
                <v-card class="my-quote">
                    <v-card-title>
                        <slot name="title"></slot>
                    </v-card-title>
                    <v-card-text>
                        <slot name="text"></slot>
                    </v-card-text>
                </v-card>

            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    export default {
        name: "Quote",
        props: {

        }
    }
</script>

<style scoped>
    .my-quote:hover {
        background-color: pink;
    }
    .my-quote:active {
        box-shadow: none;
        transform: translateY(4px);
    }
</style>