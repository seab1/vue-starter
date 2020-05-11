<template>
    <div>
        <label>Log in with e-mail</label>
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
				this.buttonLabel = 'Log in';
  			}
		},*/

		computed:
		{
			buttonLabelToDisplay() {return this.buttonLabel || 'Log in';}
		}
    }
</script>
