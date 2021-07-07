<template>
  <div class="container border-lg align-self-center">
    <div class="row justify-content-center">
      <div class="col-4">
        <div class="row">
          <div class="col-3 border" @click="state.operator = '+', operator()">
            +
          </div>
          <div class="col-3 border" @click="state.operator = '/', operator()">
            /
          </div>
          <div class="col-3 border" @click="state.operator = '*', operator()">
            *
          </div>
          <div class="col-3 border" @click="state.operator = '-', operator()">
            -
          </div>
        </div>
        <div class="row">
          <div class="col-3 border" @click="state.num += '7'">
            7
          </div>
          <div class="col-3 border" @click="state.num += '8'">
            8
          </div>
          <div class="col-3 border" @click="state.num += '9'">
            9
          </div>
          <div class="col-3 border"></div>
        </div>
        <div class="row">
          <div class="col-3 border" @click="state.num += '4'">
            4
          </div>
          <div class="col-3 border" @click="state.num += '5'">
            5
          </div>
          <div class="col-3 border" @click="state.num += '6'">
            6
          </div>
          <div class="col-3 border"></div>
        </div>
        <div class="row">
          <div class="col-3 border" @click="state.num += '1'">
            1
          </div>
          <div class="col-3 border" @click="state.num += '2'">
            2
          </div>
          <div class="col-3 border" @click="state.num += '3'">
            3
          </div>
          <div class="col-3 border" @click="clear">
            C
          </div>
        </div>
        <div class="row">
          <div class="col-3 border" @click="state.num += '0'">
            0
          </div>
          <div class="col-3 border" @click="state.num += '.'">
            .
          </div>
          <div class="col-3 border" @click="state.operator = '%', operator()">
            %
          </div>
          <div class="col-3 border" @click="enter">
            enter
          </div>
        </div>
      </div>
    </div>
    <div class="row p-5">
      <p class="pr-3">
        Results:
      </p>
      <em>{{ state.num }}</em>
      <em>{{ state.operator }}</em>
      <em>{{ state.num2 }}</em>
    </div>
  </div>
</template>

<script>
import { reactive } from '@vue/reactivity'
export default {
  name: 'Home',
  setup() {
    const state = reactive({
      num: '',
      num2: '',
      operator: ''
    })
    return {
      state,
      operator() {
        state.num2 = state.num
        state.num = ''
      },
      clear() {
        state.num = ''
        state.num2 = ''
        state.operator = ''
      },
      enter() {
        const num1 = Number(state.num)
        const num2 = Number(state.num2)
        switch (state.operator) {
          case '+' :
            state.num = num1 + num2
            break
          case '-' :
            state.num = num1 - num2
            break
          case '*' :
            state.num = num1 * num2
            break
          case '/' :
            state.num = num1 / num2
            break
          case '%' :
            state.num = num1 % num2
            break
        }
        state.operator = ''
        state.num2 = ''
      }
    }
  }
}
</script>

<style scoped lang="scss">
.col-3{
  cursor: pointer;
  transition: all .1s linear;
}
.col-3:hover{
background-color: rgba(0, 0, 0, 0.397);
}
</style>
