<template>
    <div class="container">
        <h3 class="font-weight-bold"> Searching </h3>

        <b-form-group id="input-group-1" label="Enter Number" label-for="input-1">
            <b-form-input id="input-1" v-model="key" type="email" required placeholder="Enter email">
            </b-form-input>
            <b-btn variant="success mt-2" v-on:click="linearSearch()" class="btn-block">Search</b-btn>
        </b-form-group>

        <div id="found"></div>

{{key}}
    <div class="">
       <div class="shadow-sm d-inline-block m-3 found" v-for="num in nums" :key="num.id">
       <b-btn :variant="num.variant" class="p-5"></b-btn>
        <p class="font-weight-bold mt-1 found">{{num.val}}</p>
       </div>

    </div>


    </div>
</template>
<script>
  export default {
    data() {
      return {
        mainProps: { blank: true, width: 75, height: 75, class: 'm1' },
        nums : [],
        key : '',
        timer : null
      }
    },
    mounted() {
        this.fillNumer()
    },
    methods: {
        fillNumer(){
            for(var i =0 ;i <8 ;i++){
                let val = Math.floor(Math.random() * 100)
                this.nums.push({'id': i, 'val': val, 'variant' :'primary'})
            }
        },
        time(i){
setTimeout(()=>{
              this.nums[i].variant = "success"
            }, 1000 * i)
        },
        linearSearch(){


           var node = document.createElement('h4')
             var temp=  document.getElementById('found')
             let bool = false
            let i=0
             setInterval(()=>{
            for(i=0;i<this.nums.length;i++){
            this.time(i)
            var item = document.getElementsByClassName('shadow-sm')[i].lastChild.textContent
            if(item == this.key){
              this.nums[i].variant = "danger"
            node.textContent = `Element found!! Index is ${i}`
            temp.appendChild(node)
            bool = true
            break
            }

            } }, 1000 )
           
            if(!bool && i >= this.nums.length){
               node.textContent = `Not Found`
            temp.appendChild(node)
            }

           return;
          
        }
    }

  }
</script>

<style >

.found{
  background-color: #fff !important;
 
  transition: cubic-bezier(0.075, 0.82, 0.165, 1);
  -webkit-animation: glow 1s ease-in-out infinite alternate;
  -moz-animation: glow 1s ease-in-out infinite alternate;
  animation: glow 1s ease-in-out infinite alternate;
}

@-webkit-keyframes found {
  from {
    text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px #e60073, 0 0 40px #e60073, 0 0 50px #e60073, 0 0 60px #e60073, 0 0 70px #e60073;
  }
  to {
    text-shadow: 0 0 20px #fff, 0 0 30px #ff4da6, 0 0 40px #ff4da6, 0 0 50px #ff4da6, 0 0 60px #ff4da6, 0 0 70px #ff4da6, 0 0 80px #ff4da6;
  }
}
</style>