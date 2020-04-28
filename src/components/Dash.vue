<template>
	<div>
		<!-- <div id="header">
			<div class="header__row">
				<div v-if="headerText" class="header__text">
					<span class="selected"> Selected: </span>
					<span class="name"> {{headerText}} </span>
				</div>
			</div>
		</div> -->

		<div id="content">

			<div id="leftPanelContainer" class="panelContainer default" >

				<div id="canvas" class="panel" >
					<div class="canvas__header">
						<div id="canvas__title">
							Title
						</div>
					</div>

					<div id="canvas__graph" tabindex="0">
						Graph
					</div>
				</div>

				<!-- Toolbar below graph -->
				<div id="toolbar" class="panel buttonRow">
					<div class="buttonRow__button" @click="onClickAutoLayout" title="Center Graph">
						<div><i class="fad fa-dot-circle"> </i> Center
						</div>
					</div>

					<div class="buttonRow__button" @click="onClickEditActivity" title="Edit Activity">
						<div><i class="fad fa-tasks"> </i> Activity
						</div>
					</div>

					<div class="buttonRow__button" @click='onClickToggleLocations' title="Show/Hide Locations">
						<div><i class="fad fa-clipboard-list-check"></i> Locations
						</div>
					</div>

					<div class="buttonRow__button" @click="" title="">
						<div><i class="fad fa-arrow-to-bottom"></i></i> Image
						</div>
					</div>

				</div>
			</div>

			<!-- Collapsible panels -->

			<CollapsiblePanel :minimised="minimised.Store" panelName="Store" key="Store">
					<!-- <StoreDisplay v-if="!minimised.Store">
					</StoreDisplay> -->
				</CollapsiblePanel>

			<CollapsiblePanel :minimised="minimised.Locations" panelName="Locations" key="Location">
					<!-- <Locations v-if="!minimised.Locations">
					</Locations> -->
				</CollapsiblePanel>



		</div>
	</div>
</template>

<script>
import CollapsiblePanel from '@/components/CollapsiblePanel'

import { EventBus } from '@/components/eventbus'


export default {
	name: 'Dash',
	components: {
		CollapsiblePanel,


	},

	data(){
		return{
			// Minimised States for collapsible panels
			minimised: {
				Store: true,
				Related: true,
				Locations: true
			},
		}
	},

	computed:{
		headerText(){
			return 'headerText'
		},

	},

	mounted(){
			EventBus.$on('toggleCollapsiblePanel', (panelId) => this.toggleCollapsiblePanel(panelId))
	},

	methods: {


		onClickSearch(){

			this.$modal.show(
				SearchSelectorModal,
				{

				},
				{
					draggable: true,
					height: 'auto'
				}
			)
		},

		toggleCollapsiblePanel(panelId){
			this.minimised[panelId] = ! this.minimised[panelId]
			setTimeout( ()=> this.onClickAutoLayout(), 550)
		},


	},

}
</script>


<style src='@/style/style.css'></style>

<style scoped>
#header{
	border-top: 2px solid orange;
	border-bottom: 2px solid orange;
}
.header__text{
  display: flex;
  align-items: center;
}

.header__text .selected{
	color: darkgrey
}
.header__text .name{
	margin-left: 10px;
	color: white;
	font-size: 2rem;
}


</style>
