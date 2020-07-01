<template>
  <div class="hello">
    <h1 class="font-weight-bold text-uppercase">{{ msg }}</h1>

    <div class="container shadow p-5 mt-5">
      <!-- <b-progress value="57" max="100" class="mb-3" show-value variant="danger"></b-progress> -->
      <div v-for="bar in bars" class="row mb-1" :key="bar.id">
        <div class="col-sm-12 pt-2">
          <b-progress :value="bar.value" class="popupBlocks" show-value :variant="bar.variant" :key="bar.id"></b-progress>
        </div>
      </div>



    </div>

    <div class="container mt-5">
      <div class="row">
        <div class="col-lg-4">
          <div>
            <select class="custom-select" id="inputGroupSelect01">
              <option>Choose...</option>
              <option value="bubble">Bubble</option>
              <option value="merge">Merge</option>
              <option value="insertion">Insertion</option>
            </select>
          </div>
        </div>
        
        <div class="col-lg-4">
          <button class="btn btn-primary" v-on:click="draw()">Reset Array</button>
          <button class="btn btn-info ml-5" v-on:click="bubbleSort()">Sort</button>
        </div>
      </div>

    </div>

  </div>
</template>

<script>
  export default {
    name: 'Main',
    props: {
      msg: String
    },
    data() {
      return {
        variant: ['success', 'danger', 'dark', 'warning', 'primary', 'info'],
        array: [],
        bars: [],
      }
    },
    mounted() {

      this.draw()

    },
    methods: {
      draw() {
        console.log("mounted")
        if (this.bars.length > 0) {
          this.bars = []
          this.array = []
        }
        for (var i = 0; i < 10; i++) {
          let num = Math.floor(Math.random() * 100);
          let variant = this.variant[num % 6];
          this.array.push(num)
          this.bars.push({
            'id': i,
            'variant': variant,
            'value': num
          })
        }

      },
      bubbleSort() {
        var array = this.array
        let count = 1
        console.log(this.array)
        setTimeout(() => {
          for (var i = 0; i < array.length; i++) {
            for (var j = i; j < array.length; j++) {
              if (array[i] > array[j]) {
                var temp_bar = this.bars[i].value
                this.bars[i].value = this.bars[j].value
                this.bars[j].value = temp_bar
                var temp = array[i];
                array[i] = array[j];
                array[j] = temp;
              }
            } 
          }
          }, 2000 * count++)
       
      }
    }
  }
</script>

<style>

.popupBlocks {
    animation-name: popupBlock;
    animation-timing-function: ease-in;
    animation-duration: 400ms;
    animation-delay: 400ms;
    animation-fill-mode: forwards;
    animation-direction: normal;
    transform-origin: center;
    transform-box: fill-box;
}
</style>