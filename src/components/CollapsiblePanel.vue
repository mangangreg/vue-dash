<template>
	<div class="panelContainer panelContainer--collapsible panel"
		:class="{minimised:minimised}"
		:panelName="panelName"
	>
		<slot>
			<div class="button" @click="maximise">
					<i class="fad fa-plus-hexagon" ></i>
			</div>
			<div class="title">
				{{ panelName }}
			</div>
		</slot>
	</div>

</template>

<script>
import { EventBus } from '@/components/eventbus'
export default {
	name: 'CollapsiblePanel',
	props:{
		panelName: String,
		minimised: Boolean,
	},

	methods :{
		maximise(){
			let panelId = this.panelName.replace(' ','')
			EventBus.$emit('toggleCollapsiblePanel', panelId)
		}
	}
}

</script>

<style scoped>
	.panelContainer--collapsible{
		width: 450px;
		height: 100%;
	}

	.panelContainer--collapsible[panelName="Related"]{
		width: 650px;
	}

	.panel.minimised {
		width: 50px;
		background: #cdc17b
	}
	>>> .collapsiblePanel__container{
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
	}

	>>> .collapsiblePanel__header{
		color: white;
		background-color: #3961f1;
		padding: 0.5rem;
	}

	>>> .collapsiblePanel__header .title{
		text-align: center;
		font-size: 1.4rem;
		font-weight: 500;
		margin-bottom: 0.5rem;
	}

	>>> .collapsiblePanel__header .title span{
		color: white;
	}

	>>> .collapsiblePanel__header .detailsRow{
		display: flex;
		justify-content: space-between;
	}

	>>> .collapsiblePanel__header .minimiseRow{
		font-size: 1.5rem;
		width: 100%;
		display: flex;
		justify-content: flex-end;
	}

	>>> .collapsiblePanel__body{
		flex-grow:1
	}

	>>> .collapsiblePanel__body .placeholder{
		/* margin-top: 1rem; */
		display: flex;
		justify-content: center;
		color: lightgrey;
		border-bottom: 2px solid #ececec;
		padding: 0.5rem;
		margin-top: 0!important;
	}

	.panel.minimised .title {
		 writing-mode: vertical-lr;
		font-weight:600;
		margin-top: 1rem;
		font-size: 2rem;
		color: white;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	 .panel.minimised .button {
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 1.5rem;
		color: white;
		height: 2rem;

	}
	.collapsiblePanel__Container{
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
	}

</style>
