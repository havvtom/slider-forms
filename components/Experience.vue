<template>
	<div>
		<div class="text-info mb-2" >
		  Please list your previous employment below, you can add more by clicking the "Add More" button.
		</div>
		<div class="more_experience border border-primary p-2 mb-2" 
			v-for="(experience, index) in experiences"
			:key="index"
		>
			<div class="bg-secondary py-2 mt-3">
			<div class="first_element d-md-flex ">
                  <div class="col-md-6">
                    <b-form-group id="`${index}`" 
                      label="Job Title" 
                      label-for="`job_title_held_${index}`" 
                      description=""
                    >
                      <b-form-input 
                        id="`job_title_held_${index}`" 
                        name="`job_title_held_${index}`"
                        v-model="experience.job_title_held"
                        required 
                        placeholder="i.e Developer"
                      ></b-form-input>
                    </b-form-group>
                  </div>
                  <div class="col-md-6">
                    <b-form-group
                      id="worked_at"
                      label="Company Name"                     
                      label-for="worked_at"
                      description=""
                    >
                      <b-form-input
                        id="worked_at"
                        type="text"
                        v-model="experience.company"
                        required
                      ></b-form-input>                  
                    </b-form-group>
                  </div>
                </div> 
                <div class="d-flex flex-wrap">
                    <div class="col-md-6 school">
                      <b-form-group>
                        <label for="finish-datepicker">Start Date</label>
                        <client-only><date-picker
                          :minimumView="'month'" :maximumView="'month'"
                          class="w-100"
                          placeholder="MM/YYYY"
                          format="MM/yyyy"
						 />
                        </client-only>
                      </b-form-group>
                    </div>
                    <div class="col-md-6">
                      <b-form-group>
                        <label for="finish-datepicker">End Date</label>
                        <client-only><date-picker
                          :minimumView="'month'" :maximumView="'month'"
                          class="w-100"
                          placeholder="MM/YYYY"
                          format="MM/yyyy"
                        />
                        </client-only>
                      </b-form-group>
                    </div>
                  </div>
			<!-- <input type="" name="">
			<button @click.prevent="addMore">Add More</button> -->
		</div>	
		<div class="d-flex pt-3 justify-content-end">
			<b-button variant="secondary" v-if="index != 0" @click.prevent="removeExperience(index)">
				<i class="fas fa-trash-alt"></i>
			</b-button>
		</div>
		</div>	
		<div class="d-flex pt-3 justify-content-end">
			<b-button variant="secondary" @click.prevent="addMore">Add More</b-button>
		</div>		
	</div>
</template>
<script type="text/javascript">
	export default {
		data () {
			return {
				experiences: [{job_title_held: '', company: ''}]
			}
		},
		methods: {
			addMore () {
				this.experiences.push({company: ''})
			},
			removeExperience (i) {
				this.experiences.splice(i, 1)
			}
		},
	}
</script>