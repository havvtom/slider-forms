<template>
	<div class="d-md-flex justify-content-between bg-secondary py-2 mb-2">
		<div class="col-md-6">
			<b-form-group id="input-province" label="Province" label-for="current_location">
              <b-form-select
                id="province"
                v-model="form.province"
                :options="provinces"
                v-validate="'required'" name="province" :class="{'input': true, 'is-invalid': errors.has('province') }"
              ></b-form-select>
               <b-form-invalid-feedback>{{ errors.first('province') }}</b-form-invalid-feedback>
            </b-form-group>
		</div>
		<div class="col-md-6">
			<b-form-group id="input-town" label="Town" label-for="current_location">
              <b-form-select
                id="town"
                v-model="form.town"
                :options="provinces[form.province - 1].towns"
                v-validate="'required'" name="town" :class="{'input': true, 'is-invalid': errors.has('town') }"
              ></b-form-select>
               <b-form-invalid-feedback>{{ errors.first('town') }}</b-form-invalid-feedback>
            </b-form-group>
		</div>
	</div>
</template>
<script type="text/javascript">
	export default {
		data () {
			return {
				provinces: [
					{ text: 'Eastern Cape', value: '1', towns: [ { text: 'Port Elizabeth', value: 1 }, { text: 'Uitenhage', value: 2 }, { text: 'East London', value: 3 }, { text: 'Grahamstown', value: 4 }, { text: 'Jeffreys Bay', value: 5 }, { text: 'Sunshine Coast', value: 6 }, { text: 'Wild Coast', value: 7 }, { text: 'Frontier Country', value: 8 }, { text: 'Karoo Hartland', value: 9 }, { text: 'Graaf Reinet', value: 10 }, { text: 'Queenstown', value: 11 }, { text: 'Cradock', value: 12 } ]}, { text: 'Free State', value: '2', towns: [ { text: 'Bloemfontein', value: 1 }, { text: 'Sasolburg', value: 2 }, { text: 'Parys', value: 3 }, { text: 'Welkom', value: 4 }, { text: 'Kroonstad', value: 5 }, { text: 'Virginia', value: 6 }, { text: 'Free State -North', value: 7 }, { text: 'Free State -South', value: 2 } ]}, { text: 'Gauteng', value: '3', towns: [ { text: 'Johannesburg', value: 1 }, { text: 'Pretoria', value: 2 }, { text: 'Bronkhorstspruit', value: 3 }, { text: 'Cullinan', value: 4 }, { text: 'Ekangala', value: 5 }, { text: 'Ga -Rankuwa', value: 6 }, { text: 'Hammanskraal', value: 7 }, { text: 'Mabopane', value: 8 }, { text: 'Soshanguve', value: 9 }, { text: 'Centurion', value: 10 } ]}, { text: 'Kwazulu Natal', value: '4', towns: [ { text: 'Durban', value: 1 }, { text: 'Ballito', value: 2 }, { text: 'Drakensburg', value: 3 }, { text: 'Empangeni', value: 4 }, { text: 'Natal Midlands', value: 5 }, { text: 'North Coast', value: 6 }, { text: 'Peitermaritzburg', value: 7 }, { text: 'Richards Bay', value: 8 }, { text: 'Stanger', value: 9 }, { text: 'South Coast', value: 10 }, { text: 'Zululand', value: 11 } ]}, { text: 'Limpopo', value: '5', towns: [ { text: 'Bela Bela', value: 1 }, { text: 'Polokwane', value: 2 }, { text: 'Mokopane', value: 3 }, { text: 'Tzaneen', value: 4 }, { text: 'Waterburg', value: 5 }, { text: 'Soutpansburg', value: 6 }, { text: 'Valley of the Olifants', value: 7 }, { text: 'Capricon', value: 8 }, { text: 'Lephalale', value: 9 } ]},{ text: 'Mpumalanga', value: '6', towns: [ { text: 'eMalahleni', value: 1 }, { text: 'Barberton', value: 2 }, { text: 'Delmas', value: 3 }, { text: 'Nelspruit', value: 4 }, { text: 'Secunda', value: 5 }, { text: 'Standerton', value: 6 }, { text: 'White River', value: 7 }, { text: 'Mpumalanga- North', value: 8 }, { text: 'Mpumalanga- South', value: 9 }, { text: 'Ermelo', value: 10 }, { text: 'Middleburg', value: 11 } ]}, { text: 'Northern Cape', value: '7', towns: [ { text: 'Kimberly', value: 1 }, { text: 'Upington', value: 2 }, { text: 'Kalahari', value: 3 }, { text: 'Bo Karoo', value: 4 }, { text: 'Namaqualand', value: 5 }]}, { text: 'North West', value: '8', towns: [ { text: 'Brits', value: 1 }, { text: 'Hartebeespoort', value: 2 }, { text: 'Klerksdorp', value: 3 }, { text: 'Lichtenburg', value: 4 }, { text: 'Mafikeng', value: 5 }, { text: 'Potchefstroom', value: 6 }, { text: 'Rustenburg', value: 7 }, { text: 'Vryburg', value: 8 }, { text: 'Ottosdal', value: 9 } ]}, { text: 'Western Cape', value: '9', towns: [ { text: 'Cape Town', value: 1 }, { text: 'Blouberg', value: 2 }, { text: 'Boland', value: 3 }, { text: 'Overberg', value: 4 }, { text: 'Olifantsriver', value: 5 }, { text: 'West Coast', value: 6 }, { text: 'Worcester', value: 7 }, { text: 'Garden Route', value: 8 } ]},
				],
				form: {
					province: '1',
					town: 1
				}
			}
		},
			watch: {
				'form.province' () {
					console.log(this.form.province)
				}
			}
	}
</script>