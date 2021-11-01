<script context="module" lang="ts">
	export type AlertStatus = 'warning' | 'error' | 'success' | 'info';
	export const key = { name: 'alert' };
</script>

<script lang="ts">
	import { setContext } from 'svelte';

	let clazz = '';
	export { clazz as class };
	export let status: AlertStatus = 'info';

	const classString: string = (() => {
		switch (status) {
			case 'warning':
				return 'bg-orange-200';
			case 'error':
				return 'bg-red-200';
			case 'success':
				return 'bg-green-200';
			case 'info':
			default:
				return 'bg-blue-200';
		}
	})();

	setContext(key, {
		status
	});
</script>

<div
	class={`w-full overflow-hidden flex items-center px-4 py-3 relative text-gray-700 ${classString} ${clazz}`}
	role="alert"
>
	<slot />
</div>
