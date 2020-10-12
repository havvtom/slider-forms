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
                <div class="d-md-flex justify-content-between col-12 px-0">
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-5" label="Title:" label-for="input-5">
                      <b-form-select
                        id="input-5"
                        v-model="form.title"
                        :options="titles"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-1" label="Name" label-for="input-1" description="">
                      <b-form-input id="input-1" v-model="form.name" type="text" required placeholder="name"></b-form-input>
                    </b-form-group>
                  </div>
                </div>
                <div class="d-md-flex justify-content-between col-12 px-0">
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-2" 
                      label="Surname" 
                      label-for="input-2" 
                      description=""
                    >
                      <b-form-input 
                        id="input-2" 
                        v-model="form.last_name" 
                        type="text" 
                        required 
                        placeholder="name"
                      ></b-form-input>
                    </b-form-group>
                  </div>
                  <div class="col-md-5 px-0">
                    <b-form-group
                      id="input-group-15"
                      label="Cellphone Number:"
                      label-for="cellphone"
                      description=""
                    >
                      <b-form-input
                        id="cellphone"
                        v-model="form.cellphone"
                        type="email"
                        required
                        placeholder="Enter cell number"
                      ></b-form-input>                  
                    </b-form-group>
                  </div>
                </div>               
                <div class="d-md-flex justify-content-between col-12 px-0">
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-6" label="Gender:" label-for="input-6">
                      <b-form-select
                        id="input-6"
                        v-model="form.gender"
                        :options="genders"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-7" label="Ethnic Group:" label-for="input-7">
                      <b-form-select
                        id="input-7"
                        v-model="form.ethnic_group"
                        :options="ethnic_groups"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                </div>
                <div class="d-md-flex justify-content-between col-12 px-0">
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-8" label="Nationality:" label-for="input-8">
                      <b-form-select
                        id="input-8"
                        v-model="form.nationality"
                        :options="nationalities"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-9" label="South African ID Number" label-for="input-9" description="">
                      <b-form-input id="input-9" v-model="form.id_number" type="text" required placeholder="ID Number"></b-form-input>
                    </b-form-group>
                  </div>
                </div>
                <div class="d-flex justify-content-between col-12 px-0">
                  <div class="col-md-5 px-0">
                    
                  </div>                  
                  <div class="col-5 px-0">
                    <b-form-group id="location" label="Current Living Location" label-for="input-20">
                      <b-form-select
                        id="input-20"
                        v-model="form.location"
                        :options="countries"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                </div>
                <b-form-group id="input-group-12" label="Do you have any disability?" label-for="input-12">
                  <b-form-select
                    id="input-12"
                    v-model="form.disability"
                    :options="disabilities"
                    required
                  ></b-form-select>
                </b-form-group>
                <b-button class="my-3 w-100" variant="primary" ref="nextBtn" @click.prevent="toPageTwo">
                    Next
                </b-button>
              </div>
        </div>
        <div class="col-12 page border border-primary">
          <div class="">
                <div class="title">
                  Education
                </div>
                <b-form-group id="education" label="Highest Education Qualification" label-for="education">
                  <b-form-select
                    id="education"
                    v-model="form.education"
                    :options="qualifications"
                    required
                  ></b-form-select>
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
                <b-form-group id="current_situation" label="What are you currently doing?" label-for="current_situation">
                  <b-form-select
                    id="current_situation"
                    v-model="form.current_situation"
                    :options="situations"
                    required
                  ></b-form-select>
                </b-form-group>
                <b-form-group id="previous_employment" label="What are you currently doing?" label-for="previous_employment">
                  <b-form-select
                    id="previous_employment"
                    v-model="form.previous_employment"
                    :options="employment"
                    required
                  ></b-form-select>
                </b-form-group>
                <b-form-group id="desired_job" label="Desired Job Title" label-for="desired_job" description="">
                  <b-form-input id="desired_job" v-model="form.desired_job" type="text" required placeholder="i.e Chef/Web Developer/Office Admistrator"></b-form-input>
                </b-form-group>
                <div class="d-md-flex justify-content-between col-12 px-0">
                  <div class="col-md-5 px-0">
                    <b-form-group id="salary" label="Desired Salary:" label-for="salary">
                      <b-form-select
                        id="salary"
                        v-model="form.salary"
                        :options="salaries"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                  <div class="col-md-5 px-0">
                    <b-form-group id="work_availability" label="Availability:" label-for="work_availability">
                      <b-form-select
                        id="work_availability"
                        v-model="form.availability"
                        :options="availability"
                        required
                      ></b-form-select>
                    </b-form-group>
                  </div>
                </div>
                  <div class="">Curriculum Vitae</div>
                  <b-form-file v-model="form.file" class="mt-2" plain></b-form-file>
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
                <b-form-group
                  id="input-group-3"
                  label="Email address:"
                  label-for="input-3"
                  description=""
                >
                  <b-form-input
                    id="input-3"
                    v-model="form.email"
                    type="email"
                    required
                    placeholder="Enter email"
                  ></b-form-input>
                </b-form-group>
                <b-form-group
                  id="confirm_email_address"
                  label="Confirm Email address:"
                  label-for="confirm_email"
                  description="Please re-enter your email address to confirm that you have entered it correctly."
                >
                  <b-form-input
                    id="confirm_email"
                    v-model="form.email"
                    type="email"
                    required
                    placeholder="Confirm email address"
                  ></b-form-input>
                </b-form-group>
                <b-form-group
                  id="password"
                  label="Password:"
                  label-for="password"
                  description="Your password must be 8-20 characters long, contain letters and numbers, and must not contain spaces, special characters, or emoji."
                >
                  <b-form-input
                    id="password"
                    v-model="form.password"
                    type="password"
                    required
                    placeholder="Confirm your password"
                  ></b-form-input>
                </b-form-group>
                <b-form-group
                  id="password_confirmation"
                  label="Confirm Password:"
                  label-for="password_confirmation"
                  description=""
                >
                  <b-form-input
                    id="password_confirmation"
                    v-model="form.password_confirmation"
                    type="password"
                    required
                    placeholder="Confirm your password"
                  ></b-form-input>
                </b-form-group>
                <b-form-group
                <b-form-checkbox class="mb-2 mr-sm-2 mb-sm-0">I have read and I confirm that I accept the terms and conditions of this website.</b-form-checkbox>
                <div class="field-btns d-flex justify-content-between">                    
                    <b-button type="submit" class="mt-3 prev prev-3 w-25"  @click.prevent="toPageThreePrevious" variant="primary">Previous</b-button>
                    <b-button type="submit" class="mt-3 next next-2 w-25" @click.prevent="onSubmit" variant="primary">Register</b-button>
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
          disabilities: [ { text: "No, I don't have any disabilities", value: null }, {text: 'Yes, I am disabled', value: ''} ],
          genders: [ { text: 'Please select', value: null }, {text: 'Male', value: ''}, {text: 'Female', value: ''}],
          availability: [ { text: 'Please select', value: null }, {text: 'Immediate', value: ''}, {text: '7 days', value: ''}, {text: '2 weeks', value: ''}, {text: '30 days', value: ''}, {text: '1 Calendar month', value: ''}, {text: '2 Calendar months', value: ''}, {text: 'More than 2 months', value: ''} ],
          salaries: [ { text: 'Please select', value: null }, {text: '0 - 50K Annually', value: ''}, {text: '0 - 50K Annually', value: ''}, {text: '50 - 100K Annually', value: ''}, {text: '100 - 150K Annually', value: ''}, {text: '150 - 200K Annually', value: ''}, {text: '200 - 250K Annually', value: ''}, {text: '300 - 350K Annually', value: ''}, {text: '350 - 400K Annually', value: ''}, {text: '400 - 450K Annually', value: ''}, {text: '450 - 500K Annually', value: ''}, {text: '500 - 600K Annually', value: ''}, {text: '600 - 700K Annually', value: ''}, {text: '700 - 800K Annually', value: ''}, {text: '800 - 900K Annually', value: ''}, {text: '900K - 1million Annually', value: ''},
            {text: '1 - 1,25 million Annually', value: ''}, {text: '1,25 - 1,5million Annually', value: ''}, {text: '1,5 - 1,75mill Annually', value: ''}, {text: '1,75 - 2million Annually', value: ''}, {text: '2million + Annually', value: ''},],
          employment: [ { text: 'Please select', value: null }, {text: 'Yes', value: ''}, {text: 'No', value: ''} ],
          situations: [ { text: 'Please select', value: null }, {text: 'Employed', value: ''}, {text: 'Self Employed', value: ''}, {text: 'Student', value: ''},  {text: 'Graduate', value: ''},  {text: 'Unemployed', value: ''}],
          qualifications: [ { text: 'Please select', value: null }, {text: 'Busy Studying', value: ''}, {text: 'I did not finish my high school', value: ''}, {text: 'I never finished my studies', value: ''}, {text: 'Matric/Senior Certificate', value: ''}, {text: 'Diploma', value: ''}, {text: 'Degree', value: ''} ],
          countries: [ { text: 'Please select', value: null }, {text: 'South Africa', value: ''}, {text: 'Zimbabwe', value: ''}, {text: 'Malawi', value: ''}, {text: 'Namibia', value: ''}, {text: 'Ireland', value: ''}, {text: 'United Kingdom', value: ''}, {text: 'Mauritius', value: ''}, {text: 'Zambia', value: ''}, {text: 'Botswana', value: ''}, {text: 'Swaziland', value: ''}, {text: 'Trinidad and Tobago', value: ''}, {text: 'Saint Lucia (Caribbean)', value: ''}, {text: 'Canada', value: ''}, {text: 'Cameroon', value: ''}, {text: 'Finland', value: ''}, {text: 'Ethopia', value: ''}, {text: 'Nigeria', value: ''}, {text: 'Kenya', value: ''}, {text: 'Ghana', value: ''} ],
          ethnic_groups: [ { text: 'Please select', value: null }, {text: 'Caucasian White', value: ''}, {text: 'African', value: ''}, , {text: 'Asian', value: ''}, , {text: 'Indian', value: ''} ],
          nationalities: [ { text: 'Please select', value: null }, {text: 'South African Citizen', value: ''}, {text: 'Non South African Citizen', value: ''}, , {text: 'Non South African Citizen (With Work Permit)', value: ''}, , {text: 'Non South African Citizen (With Permanent Residence)', value: ''} ],
          names: [
            'Personal', 'Education', 'Experience', 'Submit'
          ],
          form: {
            title: null, 
            name: '',
            last_name: '', 
            cellphone: '',
            gender: null,
            ethnic_group: null,
            nationality: null,
            disability: null,
            location: null,
            education: null,
            previous_employment: null,
            current_situation: null,
            salary: null,
            availability: null
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
