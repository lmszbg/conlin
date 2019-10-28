<template>
	<view class="">
			<!-- <patient-card-information></patient-card-information> -->
		<!-- 	<navigator url="../../doctor-information/doctor-information">fahfkalj</navigator> -->
			
			<!-- <inspection-report></inspection-report> -->
			<bind-visit-card></bind-visit-card>
	</view>
</template>

<script>
	import patientCardInformation from '@/pages/personal/patient-card-information/patient-card-information.vue'
	import doctorInformation from '@/pages/doctor-information/doctor-information.vue'
	import inspectionReport from '@/pages/inspection-report/inspection-report.vue'
	import bindVisitCard from '@/pages/personal/bind-visit-card/bind-visit-card'
	export default {
		components:{
			patientCardInformation,
			doctorInformation,
			inspectionReport,
			bindVisitCard
		}
	}
</script>

<style>
</style>
