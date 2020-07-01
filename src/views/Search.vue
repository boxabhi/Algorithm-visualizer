<template>
    <div class="container">
        <h3 class="font-weight-bold"> Searching </h3>

        <b-form-group id="input-group-1" label="Enter Number" label-for="input-1">
            <b-form-input id="input-1" v-model="key" type="email" required placeholder="Enter email">
            </b-form-input>
            <b-btn variant="success mt-2" v-on:click="linearSearch()" class="btn-block">Search</b-btn>
        </b-form-group>

{{key}}
    <div class="">
       <div class="shadow-sm d-inline-block m-3" v-for="num in nums" :key="num.id">
        <b-img v-bind="mainProps" class="bg-info" rounded="0"  alt="Rounded image">
        </b-img>
        <p class="font-weight-bold mt-1">{{num.val}}</p>
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
        key : ''
      }
    },
    mounted() {
        this.fillNumer()
    },
    methods: {
        fillNumer(){
            for(var i =0 ;i <10 ;i++){
                let val = Math.floor(Math.random() * 100)
                this.nums.push({'id': i, val: val})
            }
        },
        linearSearch(){
 setTimeout(()=>{
            for(var i=0;i<this.nums.length;i++){
                    var element = document.getElementsByClassName('shadow-sm')[i].firstChild
           setTimeout(()=>{
           element.classList.remove("bg-info")
               element.className += " bg-success"
                }, 1000 * i)
                console.log(document.getElementsByClassName('shadow-sm')[i].firstChild)
            }
             }, 3000 )
        }
    }

  }
</script>