<template>
    <div class="msg-box">
        <div class="parent">
            <h1>parent vue</h1>
            <input type="text" class="input" placeholder="입력하면 child1 vue에 입력값이 나타난당" v-model="msg" autofocus>
            <!-- <button type="button" class="input-area__btn" title="send" @click="sendMsg(msg)">send</button> -->
            child1 에게서 받은 데이터 : {{ text }} {{ text2 }}<br><br>
            <!-- 자식에게서 받은 데이터 : {{ text2 }} -->
            <br><br>
            <button type="button" @click="openChild2">child2 열기</button>
            <div>child2에서 받은 메시지 : {{ modalMSG }}</div>
            <br><br>
            <button type="button" @click="props3Send()">child3한테 메시지 보내기</button>
            <div>child3에서 받은 메시지 : {{ emit3MSG }}</div>
        </div>
        <Child :msg="msg" @event1="val => text = val" @event2="val => text2 = val" />
        <Child2 v-show="isVisible" @isVisible="val => isVisible = val" @modalText="val => modalMSG = val"/>        
        <Child3 :props3="props3" @emit3="val => emit3MSG = val"/>
    </div>
</template>
<script>
import Child from '@/components/Child.vue'
import Child2 from '@/components/Child2.vue'
import Child3 from '@/components/Child3.vue'

import { ref } from 'vue';

export default {
    components:{
        Child,
        Child2,
        Child3
    },
    setup() {
        let msg = ref('');
        let text = ref('');
        let text2 = ref('');
        let isVisible = ref(false);
        let modalMSG = ref('');

        let props3 = ref('');
        let emit3MSG = ref('');

        const openChild2 = () => {
            isVisible.value = !isVisible.value;
        }

        const props3Send = () => {
            props3.value = '안녕 child3 ~~'
        }

        return{
            msg, text, text2, isVisible, openChild2, modalMSG, props3, props3Send, emit3MSG
        }
    },
}
</script>