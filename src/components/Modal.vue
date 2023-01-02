<template>
    <div class="modal">
        <div class="modal__content">
            <div class="modal__header">
                <h1 class="modal__title">modal title</h1>
                <button type="button" class="modal__close" @click="hideModal">닫기</button>
            </div>
            <div class="modal__body">
                <p>{{ modalMsg }}</p>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        modalMsg: {
            type: String
        }
    },
    emits: ["isModal"],
    setup(props, context) {

        console.log(`값 : ${props.modalMsg}`);
        const { emit } = context;

        const hideModal = () => {
            emit("isModal", false)
        }

        return{
            hideModal
        }
    },
}
</script>