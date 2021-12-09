<template>
    <v-container fluid>
        <v-row>
            <v-col>
                <v-textarea
                    v-model="text"
                    hint="Text here"
                    ></v-textarea>
                <br />
                <v-btn @click="onSubmit">
                    Submit
                </v-btn>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <Note
                    :text="shown_text"
                    @clear="onClear"
                    />
            </v-col>
        </v-row>
    </v-container>
</template>
<script lang="ts">
import { defineComponent, ref, onMounted, useContext} from '@nuxtjs/composition-api'

export default defineComponent({
    setup() {
        const text = ref<string>("")
        const shown_text = ref<string>("")

        const onSubmit = () => {
            console.log("onsubmit")
            shown_text.value = text.value
            text.value = ""
        }

        const onClear = () => {
            shown_text.value = ""
        }

        const { $config } = useContext()

        onMounted(() => {
            console.log('mounted!')
            console.log($config.stage)
        })

        return {
            text,
            shown_text,
            onSubmit,
            onClear,
        }
    },
    layout: 'note',
})
</script>
