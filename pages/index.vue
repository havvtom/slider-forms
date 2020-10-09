<template>
  <div class="body d-flex">
    <div class="container">
      <header>Registration Form</header>
      <div class="progress-bar">
        <div class="step" v-for="(name, index) in names" >
          <p :ref="`p-${index}`">{{ name }}</p>
          <div class="bullet" :ref="`bullet-${index}`">
            <span>{{ index+1 }}</span>
          </div>
          <div class="check fas fa-check" :ref="`check-${index}`"></div>
        </div>
      </div>
      <div class="form-outer">
        <form>
          <div class="page" ref="slidePage" :style="style">
            <div class="title">
              Personal Information
            </div>
            <div class="field">
              <div class="label">
                First Name
              </div>
              <input type="text" />
            </div>
            <div class="field">
              <div class="label">
                Last Name
              </div>
              <input type="text" />
            </div>
            <div class="field" ref="nextBtn" @click.prevent="toPageTwo">
              <button>Next</button>
            </div>
          </div>
          <div class="page">
            <div class="title">
              Employment Status & Experience
            </div>
            <div class="field">
              <div class="label">
                First Name
              </div>
              <input type="text" />
            </div>
            <div class="field">
              <div class="label">
                Last Name
              </div>
              <input type="text" />
            </div>
            <div class="field btns">
              <button class="prev prev-1" @click.prevent="toPageOne">Previous</button>
              <button class="next next-1" @click.prevent="toPageThree">Next</button>
            </div>
          </div>
          <div class="page">
            <div class="title">
              Settings
            </div>
            <div class="field">
              <div class="label">
                First Name
              </div>
              <input type="text" />
            </div>
            <div class="field">
              <div class="label">
                Last Name
              </div>
              <input type="text" />
            </div>
            <div class="field btns">
              <button class="prev prev-2" @click.prevent="toPageTwoPrevious">Previous</button>
              <button class="next next-2" @click.prevent="toPageFour">Next</button>
            </div>
          </div>
          <div class="page">
            <div class="title">
              Settings
            </div>
            <div class="field">
              <div class="label">
                First Name
              </div>
              <input type="text" />
            </div>
            <div class="field">
              <div class="label">
                Last Name
              </div>
              <input type="text" />
            </div>
            <div class="field btns">
              <button class="prev prev-3" @click.prevent="toPageThreePrevious">Previous</button>
              <button class="submit" @click.prevent="save">Submit</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
<script type="text/javascript">
    export default {
      data () {
        return {
          // active: {
          //   'background-color': '#32a852'
          // },
          max: 4,
          current: 1,
          style: '',
          names: [
            'Personal Information', 'Education', 'Experience', 'Submit'
          ]
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
        toPageTwoPrevious () {
          this.style = {
            'margin-left' : "-25%"
          }
          this.$refs["bullet-1"][0].classList.remove('active')
          this.$refs["check-1"][0].classList.remove('active')
          this.$refs["p-1"][0].classList.remove('active')
        },
        toPageThreePrevious () {
          this.style = {
            'margin-left' : "-50%"
          }
          this.$refs["bullet-2"][0].classList.remove('active')
          this.$refs["check-2"][0].classList.remove('active')
          this.$refs["p-2"][0].classList.remove('active')
        },
        toPageTwo () {
          this.style = {
            'margin-left' : "-25%"
          }
          this.$refs["bullet-0"][0].classList.add('active')
          this.$refs["check-0"][0].classList.add('active')
          this.$refs["p-0"][0].classList.add('active')

        },
        toPageThree () {
          this.style = {
            'margin-left' : "-50%"
          }
          this.$refs["bullet-1"][0].classList.add('active')
          this.$refs["check-1"][0].classList.add('active')
          this.$refs["p-1"][0].classList.add('active')
        },
        toPageFour () {
          this.style = {
            'margin-left' : "-75%"
          }
          this.$refs["bullet-2"][0].classList.add('active')
          this.$refs["check-2"][0].classList.add('active')
          this.$refs["p-2"][0].classList.add('active')
        },
        save () {
          this.$refs["bullet-3"][0].classList.add('active')
          this.$refs["check-3"][0].classList.add('active')
          this.$refs["p-3"][0].classList.add('active')
          
          setTimeout(()=>{
            alert('You have been successfully registered')
          }, 800)
        }
      }
    }
</script>