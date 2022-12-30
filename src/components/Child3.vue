<template>
    <div class="child">
        <h1>child3 vue</h1>
        <div>{{ props3 }}</div>
        <button type="button" @click="emit3Send()">부모에게 메시지 보내기</button>
    </div>
</template>
<script>
import { ref } from 'vue'

export default {
    props: {
        props3: {
            type: String
        }
    },
    emits: ["emit3"],
    setup(props, context) {
        let emit3 = ref('');

        const { emit } = context;

        const emit3Send = () => {
            emit3.value = 'child3이 parent에게 보내는 메시지';
            emit("emit3", emit3.value);
        }

        return{
            emit3Send
        }
    },
}
</script>