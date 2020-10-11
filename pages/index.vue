<template>
  <div class="body d-flex">
    <div class="container col-10 col-md-8 col-lg-6  pt-5 pr-3 pl-3 pb-3">
      <header class="mb-4">Registration Form</header>
      <!-- <div class="d-flex progress mx-5 ">
        <div class="step w-100 p-2" v-for="(name, index) in names" >
          <p :ref="`p-${index}`" class="mb-3">{{ name }}</p>
          <div class="bullet" :ref="`bullet-${index}`">
            <span>{{ index+1 }}</span>
          </div>
          <div class="check fas fa-check" :ref="`check-${index}`"></div>
        </div>
      </div> -->
      <div class="d-flex bar text-center justify-content-around bg-secondary mb-3">
        <div v-for="(name, index) in names" class="step p-2">
          <p :ref="`p-${index}`" class="mb-3">{{ name }}</p>
          <div class="bullet" :ref="`bullet-${index}`">
            <span>{{ index+1 }}</span>
          </div>
          <div class="check fas fa-check" :ref="`check-${index}`"></div>
        </div>
      </div>
      <form class="form-outer  row flex-row flex-nowrap mt-4 pb-4">
      
        <div class="col-12 page border border-primary" :style="style" >
          <div class="">
                <div class="title">
                  Personal Information
                </div>
                <b-form-group id="input-group-5" label="Title:" label-for="input-5">
                  <b-form-select
                    id="input-5"
                    v-model="form.title"
                    :options="titles"
                    required
                  ></b-form-select>
                </b-form-group>
                <b-form-group id="input-group-1" label="Name" label-for="input-1" description="your name">
                  <b-form-input id="input-1" v-model="form.name" type="text" required placeholder="name"></b-form-input>
                </b-form-group>
                <b-form-group id="input-group-2" 
                  label="Surname" 
                  label-for="input-2" 
                  description="your surname"
                >
                  <b-form-input 
                    id="input-2" 
                    v-model="form.last_name" 
                    type="text" 
                    required 
                    placeholder="name"
                  ></b-form-input>
                </b-form-group>
                <b-form-group
                  id="input-group-3"
                  label="Cellphone Number:"
                  label-for="input-3"
                  description=""
                >
                  <b-form-input
                    id="input-3"
                    v-model="form.cellphone"
                    type="email"
                    required
                    placeholder="Enter cell number"
                  ></b-form-input>                  
                </b-form-group>
                <div class="d-flex justify-content-between col-12 px-0">
                  <div class="col-5 px-0">
                    <b-form-group id="input-group-6" label="Gender:" label-for="input-6">
                      <b-form-select
                        id="input-6"
                        v-model="form.gender"
                        :options="genders"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                  <div class="col-5 px-0">
                    <b-form-group id="input-group-6" label="Gender:" label-for="input-6">
                      <b-form-select
                        id="input-6"
                        v-model="form.gender"
                        :options="genders"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                </div>
                 <b-button class="mt-3 w-100" variant="primary" ref="nextBtn" @click.prevent="toPageTwo">
                    Next
                </b-button>
              </div>
        </div>
        <div class="col-12 page border border-primary">
          <div class="">
                <div class="title">
                  Education
                </div>
                <b-form-group id="input-group-4" label="Phone Number" label-for="input-4" description="your name">
                  <b-form-input id="input-4" v-model="form.number" type="text" required placeholder="072 653 6577"></b-form-input>
                </b-form-group>
                <b-form-group id="input-group-2" 
                  label="Surname" 
                  label-for="input-2" 
                  description="your surname"
                >
                  <b-form-input 
                    id="input-2" 
                    v-model="form.last_name" 
                    type="text" 
                    required 
                    placeholder="name"
                  ></b-form-input>
                </b-form-group>
                <b-form-group
                  id="input-group-3"
                  label="Email address:"
                  label-for="input-3"
                  description="We'll never share your email with anyone else."
                >
                  <b-form-input
                    id="input-3"
                    v-model="form.email"
                    type="email"
                    required
                    placeholder="Enter email"
                  ></b-form-input>                  
                </b-form-group>
                <div class="field-btns d-flex justify-content-between">                    
                    <b-button class="mt-3 prev prev-1 w-25"  @click.prevent="toPageOne" variant="primary">Previous</b-button>
                    <b-button class="mt-3 next next-1 w-25" @click.prevent="toPageThree" variant="primary">Next</b-button>
                  </div>
              </div>
        </div>
        <div class="col-12 page border border-primary">
          <div class="page">
                <div class="title">
                  Work Experience
                </div>
                <b-form-group id="input-group-4" label="Phone Number" label-for="input-4" description="your name">
                  <b-form-input id="input-4" v-model="form.number" type="text" required placeholder="072 653 6577"></b-form-input>
                </b-form-group>
                <b-form-group id="input-group-2" 
                  label="Surname" 
                  label-for="input-2" 
                  description="your surname"
                >
                  <b-form-input 
                    id="input-2" 
                    v-model="form.last_name" 
                    type="text" 
                    required 
                    placeholder="name"
                  ></b-form-input>
                </b-form-group>
                <b-form-group
                  id="input-group-3"
                  label="Email address:"
                  label-for="input-3"
                  description="We'll never share your email with anyone else."
                >
                  <b-form-input
                    id="input-3"
                    v-model="form.email"
                    type="email"
                    required
                    placeholder="Enter email"
                  ></b-form-input>
                </b-form-group>
                <div class="field-btns d-flex justify-content-between">                    
                    <b-button class="mt-3 rev prev-2 w-25"  @click.prevent="toPageTwoPrevious" variant="primary">Previous</b-button>
                    <b-button class="mt-3 next next-2 w-25" @click.prevent="toPageFour" variant="primary">Next</b-button>
                  </div>
              </div>
        </div>
        <div class="col-12 page border border-primary">
          <div class="page">
                <div class="title">
                  Submit
                </div>
                <b-form-group id="input-group-4" label="Phone Number" label-for="input-4" description="your name">
                  <b-form-input id="input-4" v-model="form.number" type="text" required placeholder="072 653 6577"></b-form-input>
                </b-form-group>
                <b-form-group id="input-group-2" 
                  label="Surname" 
                  label-for="input-2" 
                  description="your surname"
                >
                  <b-form-input 
                    id="input-2" 
                    v-model="form.last_name" 
                    type="text" 
                    required 
                    placeholder="name"
                  ></b-form-input>
                </b-form-group>
                <b-form-group
                  id="input-group-3"
                  label="Email address:"
                  label-for="input-3"
                  description="We'll never share your email with anyone else."
                >
                  <b-form-input
                    id="input-3"
                    v-model="form.email"
                    type="email"
                    required
                    placeholder="Enter email"
                  ></b-form-input>
                </b-form-group>
                <div class="field-btns d-flex justify-content-between">                    
                    <b-button type="submit" class="mt-3 prev prev-3 w-25"  @click.prevent="toPageThreePrevious" variant="primary">Previous</b-button>
                    <b-button type="submit" class="mt-3 next next-2 w-25" @click.prevent="onSubmit" variant="primary">Save</b-button>
                  </div>
              </div>
        </div>
      </form>     
    </div>
</div> 
      </div>
    </div>
  </div>
</template>
<script type="text/javascript">
    export default {
      data() {
        return {
          style: '',
          titles: [
          {text: 'Please select some item', value: null}, { text: 'Miss', value: 'a'}, { text: 'Ms',value: 'b'}, { text: 'Mrs', value: 'c'}, { text: 'Ms',value: 'b' }, { text: 'Mr',value: 'd'
          }],
          genders: [ { text: 'Please select', value: null }, {text: 'Male', value: ''}, {text: 'Female', value: ''} ],
          names: [
            'Personal', 'Education', 'Experience', 'Submit'
          ],
          form: {
            title: null, 
            name: '',
            last_name: '', 
            cellphone: '',
            gender: null
          }
        };
      },
      methods: {
        toPageOne () {
          this.style = {
            'margin-left' : "0%"
          }
          this.$refs["bullet-0"][0].classList.remove('active')
          this.$refs["check-0"][0].classList.remove('active')
          this.$refs["p-0"][0].classList.remove('active')

        },
        toPageTwo () {
          this.style = {
            'margin-left' : "-100%"
          }
          this.$refs["bullet-0"][0].classList.add('active')
          this.$refs["check-0"][0].classList.add('active')
          this.$refs["p-0"][0].classList.add('active')
        },
        toPageTwoPrevious () {
          this.style = {
            'margin-left' : "-100%"
          }
          this.$refs["bullet-1"][0].classList.remove('active')
          this.$refs["check-1"][0].classList.remove('active')
          this.$refs["p-1"][0].classList.remove('active')
        },
        toPageThree () {
          this.style = {
            'margin-left' : "-200%"
          }
          this.$refs["bullet-1"][0].classList.add('active')
          this.$refs["check-1"][0].classList.add('active')
          this.$refs["p-1"][0].classList.add('active')
        },
        toPageThreePrevious () {
          this.style = {
            'margin-left' : "-200%"
          }
          this.$refs["bullet-2"][0].classList.remove('active')
          this.$refs["check-2"][0].classList.remove('active')
          this.$refs["p-2"][0].classList.remove('active')
        },
        toPageFour () {
          this.style = {
            'margin-left' : "-300%"
          }
          this.$refs["bullet-2"][0].classList.add('active')
          this.$refs["check-2"][0].classList.add('active')
          this.$refs["p-2"][0].classList.add('active')
        },
        onSubmit() {
          this.$refs["bullet-3"][0].classList.add('active')
          this.$refs["check-3"][0].classList.add('active')
          this.$refs["p-3"][0].classList.add('active')
          
          setTimeout(()=>{
            alert('You have been successfully registered')
          }, 800)
        },
        onReset() {}
      }
    };
</script>
