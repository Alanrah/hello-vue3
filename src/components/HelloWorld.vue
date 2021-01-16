<template>
  <!-- <div class="hello">
      <input type="number" v-model="a">
      +
      <input type="number" v-model="b">
      {{ d }}
  </div> -->
  {{ msg }}
</template>
<script lang="ts">
// vue3 可以不用 defineComponent
import { ref, computed, reactive, toRefs, onRenderTracked, onRenderTriggered } from 'vue';
export default {
    name: "helloworld",
    props: {
        msg: String,
    },
    setup(props, { emit }) {
        const a = ref(1);
        const b = ref(1);
        // function x() {

        // }       
        const state = reactive({
            d: computed(() => { return a.value + b.value; })
            // x, // 这样就不用专门 return x
        })
        const c = computed(() => {
            return a.value + b.value;
        });
        // onRenderTracked(() => {})
        // onRenderTriggered(() => {})
        return {
            a,
            b,
            c,
            ...toRefs(state)
        }
    },
    mounted() {
        console.log(1);// 可以生效
    }
}

// export default defineComponent({
//   	name: "helloworld",
//     setup(props, context) {
//         const a = ref(1);
//         const b = ref(1);
//         const c = computed(() => {
//             return a.value + b.value;
//         })
//         return {
//             a,
//             b,
//             c,
//         }
//     }
// });

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
