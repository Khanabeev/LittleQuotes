<template>
    <v-container>
        <v-row class="d-flex justify-center">
            <v-col lg="6" md="6" sm="12">
                <v-form>
                    <v-textarea
                            outlined
                            label="Enter your quote here"
                            v-model="quote"
                            :error="error"
                            rows="3"
                    ></v-textarea>
                    <v-btn :disabled="isMaximum" color="primary" @click.prevent="addQuote">Add quote</v-btn>
                </v-form>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    export default {
        name: "NewQuote",
        props: {
            isMaximum: {
                type: Boolean,
                require: true
            }
        },
        data: ()=>({
            quote: '',
            error: false
        }),

        methods: {
            addQuote: function () {
                this.error = false;
                this.quote = this.quote.trim();
                if (this.quote !== '') {
                    this.$emit('addQuote',this.quote);
                    this.quote = '';
                } else {
                    this.error = true;
                }

            }
        }
    }
</script>

<style scoped>

</style>