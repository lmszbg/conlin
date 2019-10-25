<template>
	<view class="">
			<!-- <patient-card-information></patient-card-information> -->
		<!-- 	<navigator url="../../doctor-information/doctor-information">fahfkalj</navigator> -->
			
			<inspection-report></inspection-report>
	</view>
</template>

<script>
	import patientCardInformation from '@/pages/personal/patient-card-information/patient-card-information.vue'
	import doctorInformation from '@/pages/doctor-information/doctor-information.vue'
	import inspectionReport from '@/pages/inspection-report/inspection-report.vue'
	export default {
		components:{
			patientCardInformation,
			doctorInformation,
			inspectionReport
		}
	}
</script>

<style>
</style>
