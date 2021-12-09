<template>
    <div>
        <v-card>
            <v-card-text>
                {{ text }}
            </v-card-text>
        </v-card>
        <br />
        <v-btn @click="onClear">
            clear
        </v-btn>
    </div>
</template>
<script lang="ts">
import { defineComponent, ref, SetupContext } from '@nuxtjs/composition-api'

type Props = {
    text: string,
};

export default defineComponent({
    props: {
        text: {
            type: String,
        }
    },

    setup(props: Props, context: SetupContext) {
        const title = ref<string>('Note');

        const onClear = () => {
            context.emit("clear");
        };

        return {
            title,
            onClear,
        };
    },
})
</script>
