<template>
    <div>
        <label>Zaloguj siÄ™ e-mailem</label>
        <input type="email" v-model="email">
        <button @click="enter()"> {{ buttonLabelToDisplay }}</button>
    </div>
</template>

<script>
	export default
	{
		props: ['buttonLabel'],

		data()
		{
            return {
                email: ''
            }
		},
		
		methods:
		{
			enter()
			{
                this.$emit('login', this.email);
            }
		},
		
		/*mounted()
		{
			if (!this.buttonLabel)
			{
				this.buttonLabel = 'Zaloguj siê';
  			}
		},*/

		computed:
		{
			buttonLabelToDisplay() {return this.buttonLabel || 'Zaloguj siê';}
		}
    }
</script>
