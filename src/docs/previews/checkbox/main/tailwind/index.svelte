<script lang="ts">
	import { createCheckbox, melt } from '$lib/index.js';
	import { Check, Minus } from 'lucide-svelte';

	const {
		elements: { root, input },
		helpers: { isChecked, isIndeterminate },
	} = createCheckbox({
		defaultChecked: 'indeterminate',
	});
</script>

<form>
	<div class="flex items-center justify-center">
		<button
			use:melt={$root}
			class="flex h-6 w-6 appearance-none items-center justify-center
            rounded-sm bg-white text-magnum-600 shadow-lg hover:opacity-75"
			id="checkbox"
		>
			{#if $isIndeterminate}
				<Minus class="square-4" />
			{:else if $isChecked}
				<Check class="square-4" />
			{/if}
			<input use:melt={$input} />
		</button>
		<label class="pl-[15px] text-[15px] leading-none text-white" for="checkbox">
			Accept terms and conditions.
		</label>
	</div>
</form>
