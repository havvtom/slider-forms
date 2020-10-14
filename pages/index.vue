<template>
  <div class="body d-flex">
    <div class="container col-10 col-md-8 col-lg-6  pt-5 pr-3 pl-3 pb-3">
      <header class="mb-4">Registration Form</header>
      
      <div class="bar text-center justify-content-around mb-3">
        <div v-for="(name, index) in names" class="step p-2">
          <p :ref="`p-${index}`" class="mb-3">{{ name }}</p>
          <div class="bullet" :ref="`bullet-${index}`">
            <span>{{ index+1 }}</span>
          </div>
          <div class="check fas fa-check" :ref="`check-${index}`"></div>
        </div>
      </div>
      <form class="form-outer  row flex-row flex-nowrap mt-4 pb-4">
      
        <div class="col-12 page border border-secondary" :style="style" >
          <div class="">
                <div class="title my-4">
                  Personal Information
                </div>
                <div class="d-md-flex justify-content-between col-12 px-0">
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-5" label="Title:" label-for="input-5">
                      <b-form-select
                        id="input-5"
                        v-validate="'required'" name="title" :class="{'input': true, 'is-invalid': errors.has('title') }"
                        v-model="form.title"
                        :options="titles"
                        required
                      ></b-form-select>
                      <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('title') }}</b-form-invalid-feedback>
                    </b-form-group>
                  </div>
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-1" label="Name" label-for="input-1" description=""
                    >
                      <b-form-input id="input-1" 
                        name="name"
                        v-model="form.name" type="text" 
                        required placeholder="name"
                        v-validate="'required|alpha'" :class="{'input': true, 'is-invalid': errors.has('name') }"
                      >                        
                      </b-form-input>
                      <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('name') }}</b-form-invalid-feedback>
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
                        name="surname"
                        v-validate="'required|alpha'" :class="{'input': true, 'is-invalid': errors.has('surname') }" 
                        type="text" 
                        required 
                        placeholder="Surname"
                      ></b-form-input>
                      <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('surname') }}</b-form-invalid-feedback>
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
                        type="text"
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
                        v-validate="'required'" name="gender" :class="{'input': true, 'is-invalid': errors.has('gender') }"
                      ></b-form-select>
                      <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('gender') }}</b-form-invalid-feedback>
                    </b-form-group>
                  </div>
                  <div class="col-md-5 px-0">
                    <b-form-group id="input-group-7" label="Ethnic Group:" label-for="input-7">
                      <b-form-select
                        id="input-7"
                        v-model="form.ethnic_group"
                        :options="ethnic_groups"
                        v-validate="'required'" name="ethnic" :class="{'input': true, 'is-invalid': errors.has('ethnic') }"
                      ></b-form-select>
                       <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('ethnic') }}</b-form-invalid-feedback>
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
                        v-validate="'required'" name="nationality" :class="{'input': true, 'is-invalid': errors.has('nationality') }"
                      ></b-form-select>
                      <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('nationality') }}</b-form-invalid-feedback>
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
                        v-validate="'required'" name="location" :class="{'input': true, 'is-invalid': errors.has('location') }"
                        :options="countries"
                        required
                      ></b-form-select>
                      <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('location') }}</b-form-invalid-feedback>
                    </b-form-group>
                  </div>
                </div>
                <b-form-group id="input-group-12" label="Do you have any disability?" label-for="input-12">
                  <b-form-select
                    id="input-12"
                    v-model="form.disability"
                    :options="disabilities"
                  ></b-form-select>
                </b-form-group>
                <b-form-group
                  id="disability_1"
                  :style="display_disability_1"
                  label="Please describe the nature of your disability"
                  label-for="disability_1"
                  description=""
                >
                  <b-form-input
                    id=""
                    v-model="form.disability_1"
                    type="text"
                    v-validate="'required'" name="disability_1" ref="disability_1" :class="{'input': true, 'is-invalid': errors.has('disability_1') }"
                    data-vv-as="disabilities"
                    placeholder="i.e Vision, Movement, Hearing, etc"
                  ></b-form-input>     
                  <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('disability_1') }}</b-form-invalid-feedback>             
                </b-form-group>
                <b-button class="my-3 w-100" variant="primary" ref="nextBtn" @click.prevent="toPageTwo">
                    Next
                </b-button>
              </div>
        </div>
        <div class="col-12 page border border-secondary">
          <div class="page">
                <div class="title my-4">
                  Education & Work Experience
                </div>
                <b-form-group id="education" label="Highest Education Qualification" label-for="education">
                  <b-form-select
                    id="education"
                    v-model="form.education"
                    :options="qualifications"
                    v-validate="'required'" name="education" :class="{'input': true, 'is-invalid': errors.has('education') }"
                  ></b-form-select>
                  <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('education') }}</b-form-invalid-feedback>
                </b-form-group>
                <b-form-group id="current_situation" label="What are you currently doing?" label-for="current_situation">
                  <b-form-select
                    id="current_situation"
                    v-model="form.current_situation"
                    :options="situations"
                    v-validate="'required'" name="current_situation" :class="{'input': true, 'is-invalid': errors.has('current_situation') }"
                    data-vv-as="current situation"
                  ></b-form-select>
                  <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('current_situation') }}</b-form-invalid-feedback>
                </b-form-group>
                <b-form-group id="previous_employment" label="Have you been employed previously?" label-for="previous_employment">
                  <b-form-select
                    id="previous_employment"
                    v-model="form.previous_employment"
                    :options="employment"
                    v-validate="'required'" name="previous_employment" :class="{'input': true, 'is-invalid': errors.has('previous_employment') }"
                    data-vv-as="previous employment"
                  ></b-form-select>
                  <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('previous_employment') }}</b-form-invalid-feedback>
                </b-form-group>
                <b-form-group id="desired_job" label="Desired Job Title" label-for="desired_job" description="">
                  <b-form-input id="desired_job" v-model="form.desired_job" type="text"
                    v-validate="'required'" name="desired_job" :class="{'input': true, 'is-invalid': errors.has('desired_job') }"
                    placeholder="i.e Chef/Web Developer/Office Admistrator"
                    data-vv-as="desired job"
                    >                      
                    </b-form-input>
                    <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('desired_job') }}</b-form-invalid-feedback>
                </b-form-group>
                <div class="d-md-flex justify-content-between col-12 px-0">
                  <div class="col-md-5 px-0">
                    <b-form-group id="salary" label="Desired Salary:" label-for="salary">
                      <b-form-select
                        id="salary"
                        v-model="form.salary"
                        :options="salaries"
                        v-validate="'required'" name="salary" :class="{'input': true, 'is-invalid': errors.has('salary') }"
                      ></b-form-select>
                      <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('salary') }}</b-form-invalid-feedback>
                    </b-form-group>
                  </div>
                  <div class="col-md-5 px-0">
                    <b-form-group id="work_availability" label="Availability:" label-for="work_availability">
                      <b-form-select
                        id="work_availability"
                        v-model="form.availability"
                        :options="availability"
                        v-validate="'required'" name="availability" :class="{'input': true, 'is-invalid': errors.has('availability') }"
                      ></b-form-select>
                      <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('availability') }}</b-form-invalid-feedback>
                    </b-form-group>
                  </div>
                </div>
                  <div class="">Curriculum Vitae</div>
                  <b-form-file 
                    v-model="form.file" 
                    class="mt-2" 
                    plain
                  >                      
                  </b-form-file>
                <div class="field-btns d-flex justify-content-between mb-3">                    
                    <b-button class="mt-3 rev prev-2 w-50 mr-3"  @click.prevent="toPageOne" variant="primary">Previous</b-button>
                    <b-button class="mt-3 next next-2  w-50" @click.prevent="toPageThree" variant="primary">Next</b-button>
                  </div>
              </div>
        </div>
        <div class="col-12 page border border-secondary">
          <div class="page">
                <div class="title my-4">
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
                    v-validate="'required|email'" name="email" :class="{'input': true, 'is-invalid': errors.has('email') }"
                    placeholder="Enter email"
                  ></b-form-input>
                  <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('email') }}</b-form-invalid-feedback>
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
                    v-validate="'required'" name="password" ref="password" :class="{'input': true, 'is-invalid': errors.has('password') }"
                    placeholder="Enter your password"
                  ></b-form-input>     
                  <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('password') }}</b-form-invalid-feedback>             
                </b-form-group>
                <b-form-group
                  id="password_confirmation"
                  label="Confirm Password:"                 
                  name="password_confirmation"                 
                  label-for="password_confirmation"
                  description=""
                >
                  <b-form-input
                    id="password_confirmation"
                    v-model="form.password_confirmation"
                    type="password"
                    data-vv-as="password"
                    v-validate="'required|confirmed:password'" name="password_confirmation" :class="{'input': true, 'is-invalid': errors.has('password_confirmation') }"
                    placeholder="Confirm your password"
                  ></b-form-input>
                  <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('password_confirmation') }}</b-form-invalid-feedback> 
                </b-form-group>
                <b-form-group>
                <b-form-checkbox 
                  class="mb-2 mr-sm-2 mb-sm-0"
                  v-validate="'required:true'" name="terms" :class="{'input': true, 'is-invalid': errors.has('terms') }"
                  v-model="form.terms"
                  data-vv-as="terms"
                >
                  I have read and I confirm that I accept the terms and conditions of this website.
                </b-form-checkbox>
                <b-form-invalid-feedback id="input-2-live-feedback">{{ errors.first('terms') }}</b-form-invalid-feedback>
                </b-form-group>
                <div class="field-btns d-flex justify-content-between">                    
                    <b-button type="submit" class="mt-3 prev prev-3 w-50 mr-3"  @click.prevent="toPageTwoPrevious" variant="primary">Previous</b-button>
                    <b-button type="submit" class="mt-3 next next-2 w-50" @click.prevent="onSubmit" variant="primary">Register</b-button>
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
          areValid: '',
          style: '',
          display_disability_1: '',
          titles: [
          {text: 'Please select some item', value: null}, { text: 'Miss', value: '1'}, { text: 'Ms',value: '2'}, { text: 'Mrs', value: '3'}, { text: 'Ms',value: '4' }, { text: 'Mr',value: '5'
          }],
          disabilities: [ { text: "No, I don't have any disabilities", value: '1' }, {text: 'Yes, I am disabled', value: '2'} ],
          genders: [ { text: 'Please select', value: null }, {text: 'Male', value: '1'}, {text: 'Female', value: '2'}],
          availability: [ { text: 'Please select', value: null }, {text: 'Immediate', value: '1'}, {text: '7 days', value: '2'}, {text: '2 weeks', value: '3'}, {text: '30 days', value: '4'}, {text: '1 Calendar month', value: '5'}, {text: '2 Calendar months', value: '6'}, {text: 'More than 2 months', value: '7'} ],
          salaries: [ { text: 'Please select', value: null }, {text: '0 - 50K Annually', value: '1'}, {text: '0 - 50K Annually', value: '2'}, {text: '50 - 100K Annually', value: '3'}, {text: '100 - 150K Annually', value: '4'}, {text: '150 - 200K Annually', value: '5'}, {text: '200 - 250K Annually', value: '6'}, {text: '300 - 350K Annually', value: '7'}, {text: '350 - 400K Annually', value: '8'}, {text: '400 - 450K Annually', value: '9'}, {text: '450 - 500K Annually', value: '10'}, {text: '500 - 600K Annually', value: '11'}, {text: '600 - 700K Annually', value: '12'}, {text: '700 - 800K Annually', value: '13'}, {text: '800 - 900K Annually', value: '14'}, {text: '900K - 1million Annually', value: '15'},
            {text: '1 - 1,25 million Annually', value: '16'}, {text: '1,25 - 1,5million Annually', value: '17'}, {text: '1,5 - 1,75mill Annually', value: '18'}, {text: '1,75 - 2million Annually', value: '19'}, {text: '2million + Annually', value: '20'}],
          employment: [ { text: 'Please select', value: null }, {text: 'Yes', value: '1'}, {text: 'No', value: '2'} ],
          situations: [ { text: 'Please select', value: null }, {text: 'Employed', value: '1'}, {text: 'Self Employed', value: '2'}, {text: 'Student', value: '3'},  {text: 'Graduate', value: '4'},  {text: 'Unemployed', value: '5'}],
          qualifications: [ { text: 'Please select', value: null }, {text: 'Busy Studying', value: '1'}, {text: 'I did not finish my high school', value: '2'}, {text: 'I never finished my studies', value: '3'}, {text: 'Matric/Senior Certificate', value: '4'}, {text: 'Diploma', value: '5'}, {text: 'Degree', value: '6'} ],
          countries: [ { text: 'Please select', value: null }, {text: 'South Africa', value: '1'}, {text: 'Zimbabwe', value: '2'}, {text: 'Malawi', value: '3'}, {text: 'Namibia', value: '4'}, {text: 'Ireland', value: '5'}, {text: 'United Kingdom', value: '6'}, {text: 'Mauritius', value: '7'}, {text: 'Zambia', value: '8'}, {text: 'Botswana', value: '9'}, {text: 'Swaziland', value: '10'}, {text: 'Trinidad and Tobago', value: '11'}, {text: 'Saint Lucia (Caribbean)', value: '12'}, {text: 'Canada', value: '13'}, {text: 'Cameroon', value: '14'}, {text: 'Finland', value: '15'}, {text: 'Ethopia', value: '16'}, {text: 'Nigeria', value: '17'}, {text: 'Kenya', value: '18'}, {text: 'Ghana', value: '19'} ],
          ethnic_groups: [ { text: 'Please select', value: null }, {text: 'Caucasian White', value: '1'}, {text: 'African', value: '2'}, , {text: 'Asian', value: '3'}, , {text: 'Indian', value: '4'} ],
          nationalities: [ { text: 'Please select', value: null }, {text: 'South African Citizen', value: '1'}, {text: 'Non South African Citizen', value: '2'}, , {text: 'Non South African Citizen (With Work Permit)', value: '3'}, , {text: 'Non South African Citizen (With Permanent Residence)', value: '4'} ],
          names: [
            'Personal', 'Education & Experience', 'Submit'
          ],
          form: {
            title: null, 
            name: '',
            last_name: '', 
            cellphone: '',
            gender: null,
            ethnic_group: null,
            nationality: null,
            disability: 1,
            location: null,
            education: null,
            previous_employment: null,
            current_situation: null,
            salary: null,
            availability: null,
            terms: ''
          }
        };
      },
      watch: {
            'areValid' () {
                setTimeout(()=>{
                alert('You have been successfully registered')
              }, 800)
            },
            'form.disability' () {
              if(this.form.disability == 2) {
                console.log('yeees')
                this.display_disability_1 = {
                  "display" : "block"
                }
              } else {
                this.display_disability_1 = {
                  "display" : "none"
                }
              }

              
            }
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
          var validatables = ['name', 'title', 'surname', 'ethnic', 'gender', 'nationality', 'location']
          if( this.form.disability == 2 ) {
              validatables.push('disability_1')
          }
          this.validate(validatables, "-100%", 0)        
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
          this.validate(['education', 'current_situation', 'previous_employment', 'desired_job', 'salary', 'availability'], "-200%", 1) 
          
        },
        toPageThreePrevious () {
          this.style = {
            'margin-left' : "-200%"
          }
          this.$refs["bullet-2"][0].classList.remove('active')
          this.$refs["check-2"][0].classList.remove('active')
          this.$refs["p-2"][0].classList.remove('active')
        },
        async validate (fields, moveBy, index) {
          const results = Promise.all(
              fields.map ( f => {
                return this.$validator.validate(f)
              } )
          );

          const areValid = (await results).every(isValid => isValid)

          if( areValid ) {
            this.style = {
                'margin-left' : moveBy
              }

              this.$refs[`bullet-${index}`][0].classList.add('active')
              this.$refs[`check-${index}`][0].classList.add('active')
              this.$refs[`p-${index}`][0].classList.add('active')
          }
          if( index == 2 && areValid ) {
            this.areValid =  areValid
          }
        },
        onSubmit() {
          this.validate(['email', 'password', 'password_confirmation', 'terms'], "-200%", 2) 
          
          
        },
        onReset() {}
      }
    };
</script>
