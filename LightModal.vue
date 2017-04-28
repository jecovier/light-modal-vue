<template>
	<transition
		mode="out-in"
		name = "modal"
		@enter= "enter"
		@before-leave= "leave">
		<div
			class  = "modal-mask"
			@click = "close">
			<div
				class = "modal-wrapper">
				<div
					@click.stop
					class  = "modal-container animated"
					:class = "animation">
					<div
						class="modal-header">
						<slot
							name="modal-header">
							{{title}}
							<button
								class  = "modal-default-button"
								@click = "close">
								X
							</button>
						</slot>
					</div>

					<div
						class = "modal-body">
						<slot
							name = "modal-body">
							default body
						</slot>
					</div>

					<div
						class = "modal-footer">
						<slot
							name = "modal-footer">
							<button
								class  = "modal-default-button"
								@click = "close">
								OK
							</button>
						</slot>
					</div>
				</div><!-- Modal-container end -->
			</div><!-- Modal-wrapper end -->
		</div><!-- Modal-mask end -->
	</transition>
</template>



<script>
export default {
	data: function(){
		return {
			animate   : true,
			animation : '',
		}
	},
	props: [
		'title',
		'intro',
		'outro'
	],
	computed:{
		animation_in: function(){
			if( this.intro === undefined )
				return 'default';
			if( this.intro === 'none' )
				return '';
			return this.intro;
		},
		animation_out: function(){
			if( this.outro === undefined )
				return 'default';
			if( this.outro === 'none' )
				return '';
			return this.outro;
		}
	},
	created: function () {
		document.addEventListener("keydown", (e) => {
			if (e.keyCode == 27)
				this.close();
		});
	},
	methods: {
		close: function() {
			this.$emit('close');
		},
		enter: function(){
			this.animation = this.animation_in;
		},
		leave: function(){
			this.animation = this.animation_out;
		}
	}
}
</script>


<!-- my-component.vue -->
<style lang="sass">
	@import "main.scss"
</style>
