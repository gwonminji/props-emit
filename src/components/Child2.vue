<template>
    <div class="child">
        <h1>child2 vue</h1>
        <button type="button" @click="send">숨어버리기</button>
    </div>
</template>
<script>
export default {
    emits:["isVisible", "modalText"],
    setup(props, context) {
        let { emit } = context;

        let send = () => {
            emit("isVisible", false);
            emit("modalText", "난 사라질거야~~");
        }
        return{
            send
        }
    },
}
</script>