<template>
  <div class="child">
    <h1>child1 vue</h1>
    <p>parent vue에서 받은 메시지 : {{ msg }}</p>
    <br>
    <button type="button" @click="sendMsg">메시지 보내기</button>
    <!-- <button type="button" @click="sendMsg2">잘가라고 보내기</button> -->

  </div>
</template>

<script>
// import { onMounted } from '@vue/runtime-core'
export default {
  props: {
    msg: {
      type: String
    }
  },
  emits: ["event1", "event2"],
  setup(props, context){
    const { emit } = context;

    const sendMsg = () => {
      // emit("event1", "안녕");
      // emit("event2", "잘가");
      emit("event1", `"${props.msg}"(이)라고 보냈었지?`);
    }

    const sendMsg2 = () => {
      emit("event2", "잘가");
    }

    return{
      sendMsg, sendMsg2
    }
  }
}
</script>