<template>
    <div class="child">
        <h1>child4 vue</h1>
        <div>{{ props4 }}</div>
        <p>select 하면 select한 값 부모에게 보내기</p>
        <!-- <select name="" id="" v-model="value" @change="isSelected">
            <option value="0" selected>0</option>
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
        </select> -->
        <select name="" id="" v-model="isValue" @change="isChange">
            <option value="0" selected>0번</option>
            <option value="1">1번</option>
            <option value="2">2번</option>
            <option value="3">3번</option>
            <option value="4">4번</option>
        </select>
        <div v-show="isVisible" class="modal">
            <div class="modal__content">
                <div class="modal__header">
                    <h1 class="modal__title">modal title</h1>
                    <button type="button" class="modal__close" @click="hideModal">닫기</button>
                </div>
                <div class="modal__body">
                    <p>{{ isValue }} 번을 선택함</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { ref } from 'vue';

export default {
    props: {
        props4: {
            type: String
        }
    },
    setup() {
        let isValue = ref('');
        let isVisible = ref(false);

        const isChange = () => {
            // isValue
            console.log(isValue.value)
            // console.log("isChange");
            isVisible.value = true;
        }

        const hideModal = () => {
            isVisible.value = false;
        }

        return{
            isValue, isVisible, isChange, hideModal
        }
    },
}
</script>