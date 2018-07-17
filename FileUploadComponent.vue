<template>
    <v-container
            class="file-upload-component pa-0"
            grid-list-xl
            fluid>
        <v-layout wrap>
            <v-flex xs12>
                <v-text-field
                        :label="label"
                        :error-messages="errorMessages"
                        @focus="pickFile"
                        @click:prepend="pickFile"
                        prepend-icon="attachment"
                        :value="name"
                        :hint="hint"
                        readonly></v-text-field>

                <input
                        type="file"
                        style="display: none"
                        ref="file"
                        :accept="accept"
                        @change="onFilePicked">
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
    export default {
        name: 'v-file-upload',
        data: () => ({
            url: '',
            name: '',
            file: null,
            uploadFile: null,
        }),
        props: {
            accept: String,
            errorMessages: Array,
            label: String,
            hint: String,
        },
        methods: {
            pickFile () {
                this.$refs.file.click ();
            },

            onFilePicked (e) {
                const files = e.target.files;
                if(files[0] !== undefined) {
                    this.name = files[0].name;
                    if(this.name.lastIndexOf('.') <= 0) {
                        return;
                    }
                    const fr = new FileReader ();
                    fr.readAsDataURL(files[0]);
                    fr.addEventListener('load', () => {
                        this.url = fr.result;
                        this.uploadFile = files[0];
                        this.$emit('input', files[0]);
                    })
                } else {
                    this.name = '';
                    this.url = '';
                    this.uploadFile = null;
                    this.$emit('input', null);
                }


            }
        }
    }
</script>
