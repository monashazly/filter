<template >
  <div id="mainrtl"  style="font-family: 'Oxygen', sans-serif; " class="flex1">
    <div>
      <b-button class="filter" v-b-toggle.sidebar-backdrop
        ><i class="fas fa-sort-amount-down me-2"></i>Filter</b-button
      >

      <b-sidebar class="fixed-right"
        id="sidebar-backdrop"
        title="Filter"
        :backdrop-variant="variant"
        backdrop
        shadow
      >
        <div class="px-3 py-2">
          <b-form-group  label-for="backdrop-variant">
            <h5 style="font-size:15px;color:rgb(233, 158, 20)" class="mb-2">Theme</h5>
            <b-form-select
              id="backdrop-variant"
              v-model="variant"
              :options="variants"
            ></b-form-select>
          </b-form-group>
        </div>
        <hr />
        <div>
          <div v-b-toggle.sidebar-1 class="flex2 container mt-3">
            <div v-b-toggle.sidebar-1>Brand</div>
            <div v-b-toggle.sidebar-1><i class="fas fa-chevron-right"></i></div>
          </div>

          <b-sidebar id="sidebar-1" shadow>
            <div class="px-3 py-2"></div>
          </b-sidebar>
        </div>
        <div>
          <div v-b-toggle.sidebar-2 class="flex2 container mt-3">
            <div v-b-toggle.sidebar-2>Color</div>
            <div v-b-toggle.sidebar-2><i class="fas fa-chevron-right"></i></div>
          </div>

          <b-sidebar  title="Colors" id="sidebar-2" shadow>
            <div class="px-3 py-2 ">
              <div class="flex3 container ">
                <div>
                     <div class="form-check" v-for="coll in colors" :key="coll">
                  <input
                    class="form-check-input"
                    type="checkbox"
                    value=""
                    id="flexCheckDefault"
                  />
                  <label class="form-check-label" for="flexCheckDefault">
                    {{ coll }}
                  </label>
                </div>
                </div>
             <div>
                   <div v-for="coll in colors" :key="coll"
                  class="bc"
                   :style="{backgroundColor:coll}">
              
                  
                </div>
             </div>
            
              </div>
              <!-- Show Results .................. -->
              <div class="showResults mt-5">Show Results</div>
            </div>
          </b-sidebar>
        </div>
        <div>
          <!-- Sizeeeeeee -->
          <div v-b-toggle.sidebar-3 class="flex2 container mt-3">
            <div >Size</div>
            <div ><i class="fas fa-chevron-right"></i></div>
          </div>

          <b-sidebar title="Size" id="sidebar-3" shadow>
            <div class="px-3 py-2   ">
              <div class="row ms-3">
                  <div   class="col-3 mt-4 boxx shadow-sm "  v-for="box in boxes" :key="box" v-on:click="addClass" :class="isAddClass" >
                {{box}}

              </div>
              </div>
              
            <div style="margin-top:400px" class="showResults  ">Show Results</div>
              
            </div>
          </b-sidebar>
        </div>
        <div>
          <div  v-b-toggle.sidebar-4 class="flex2 container mt-3">
            <div v-b-toggle.sidebar-4>Price</div>
            <div v-b-toggle.sidebar-4><i class="fas fa-chevron-right"></i></div>
          </div>

          <b-sidebar title="Price" id="sidebar-4" shadow>
            <div class="px-3 py-2">
                <div class="rangee ">
                  <div class="container  ">
                     <div >
                    <label class="mt-2" for="range-2"><b>Select Maximum Price</b></label>
                  </div>
                  <b-form-input class="mt-4"  id="range-2" v-model="value" type="range" min="0" max="1000" step="100"></b-form-input>
                  <div class="mt-2">Max Price : {{ value }}</div>
                  </div>
                 
    
    
    
  </div>
            </div>
          </b-sidebar>
        </div>
        <div class="showResults ">Show Results</div>
      </b-sidebar>
    </div>
    <!-- Second Button ـــــــــــــــــــــ -->
    <div>
    <b-button class="ms-5 filter sort" v-b-toggle.sidebar-backdrop2><i class="fas fa-sort me-2"></i> Sort</b-button>

    <b-sidebar
      id="sidebar-backdrop2"
      title="Sidebar with backdrop"
      :backdrop-variant="variant"
      backdrop
      shadow
    >
      <div class="px-3 py-2">
        <b-form-group label="Backdrop variant" label-for="backdrop-variant">
          <b-form-select id="backdrop-variant" v-model="variant" :options="variants"></b-form-select>
        </b-form-group>
      </div>
    </b-sidebar>
  </div>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  props: {
    msg: String,
  },
  
   methods: {
            addClass: function() {
                this.isAddClass = true;
        }
    },
    
  


  data() {
    return {
      isAddClass: false,
      variant: "dark",
      variants: [
        "transparent",
        "white",
        "light",
        "dark",
        "primary",
        "secondary",
        "success",
        "danger",
        "warning",
        "info",
      ],
      value: '0',
      sidebarcon: [
        "Brands",
        "Size",
        "Color",
        "Price",
        "Fabric",
        "Length",
        "Style",
      ],
      
      colors: ['red', 'blue', 'silver','purple','fuchsia','green','olive','yellow','teal','lightpink','maroon','mediumaquamarine','mediumpurple','orchid','	peru','plum','black'],
      boxes:['42','44','46','48','50','52']
          
      
       
      
    }
  }
}

      
    
  

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#sidebar-backdrop{
  

}
.flex1 {
  display: flex;
  justify-content:center;
  margin: 20px;
  
}

.filter {
  background: white;
  color: black;
  padding: 6px 20px;
}
.flex2 {
  display: flex;
  justify-content: space-between;
}
.flex2:hover{
  background-color: rgba(230, 152, 50, 0.877);
  color: white;
}
.flex3 {
  display: flex;
  justify-content: space-between;
}
.bc{
  border:1px solid;
 
  margin: 10.5px;
  border-style: none;
  height: 15px;
  width: 15px;
}
.showResults{
  background: rgb(233, 158, 20);
  color: white;
  width: 75%;
  margin: auto;
  text-align: center;
  border:1px solid;
  border-style: none;
  border-radius: 3px;
  height: 29px;
  margin-top: 340px;
  
  

  
}
.showResults:hover{
  cursor: pointer;
  background-color: rgba(233, 158, 20, 0.719);
 
}
.sidecolor{
  background-color:white;
}
/* input[type=range]{
    -webkit-appearance: none;
    width: 290px;
}

input[type=range]::-webkit-slider-runnable-track {
    width: 500px;
    height: 5px;
    background: rgb(221, 221, 221);
    border: none;
    border-radius: 3px;
}

input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none;
    border: none;
    height: 16px;
    width: 16px;
    border-radius: 50%;
    background: goldenrod;
    margin-top: -4px;
}

input[type=range]:focus {
    outline: none;
}

input[type=range]:focus::-webkit-slider-runnable-track {
    background: rgb(204, 204, 204);
} */
@media screen and (-webkit-min-device-pixel-ratio:0) {
    input[type='range'] {
      overflow: hidden;
      width: 250px;
      -webkit-appearance: none;
      background-color: #aaaaa7;
      height: 4px;
    }
    
    input[type='range']::-webkit-slider-runnable-track {
      height: 10px;
      -webkit-appearance: none;
      color: #13bba4;
      margin-top: -1px;
        border: none;
    border-radius: 3px;
     
    }
    
    input[type='range']::-webkit-slider-thumb {
      
      -webkit-appearance: none;
     
      cursor: pointer;
      
      box-shadow: -160px 0 0 160px #e7a221;
        border: 1px solid gray;
    height: 30px;
    width: 16px;
    border-radius: 50%;
    background: rgb(224, 221, 215);
    margin-top: -4px;
    }

}
.rangee{
  background-color: white;
  height: 500px;
}
.boxx{
  background-color: white;
  height: 40px;
 margin :3px;
  text-align: center;
  /*  */
  border :1px solid gainsboro;
    border-radius: 4px;
  
  vertical-align: middle;
line-height: 34px;

}
.boxx:hover{
  cursor: pointer;
}
.boxx:active{
  background-color: coral;
}
/* #mainrtl{
  direction: rtl;
} */
/* #sidebar-backdrop.toggled{
  float: right !important;
} */




</style>
