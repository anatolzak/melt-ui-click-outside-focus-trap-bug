<script lang="ts">
	import { createDialog, melt } from '@melt-ui/svelte';

	const {
		elements: { trigger, overlay, content, title, description, close, portalled },
		states: { open }
	} = createDialog({ closeOnOutsideClick: false, forceVisible: true });
</script>

<button
	use:melt={$trigger}
	class="inline-flex items-center justify-center rounded-md bg-gray-950 px-4 py-2 font-medium leading-none text-blue-700 shadow-lg focus-within:border-4 focus-within:border-red-500 focus-within:shadow-blue-400 focus-within:outline-none hover:opacity-75"
>
	Open Dialog
</button>
{#if $open}
	<div class="" use:melt={$portalled}>
		<div use:melt={$overlay} class="fixed inset-0 z-50 bg-black/50" />
		<button
			use:melt={$close}
			class="fixed right-[10px] top-[10px] z-50 inline-flex h-6 w-6 appearance-none items-center justify-center rounded-full text-blue-800 focus-within:border-4 focus-within:border-red-500 focus-within:shadow-blue-400 focus-within:outline-none hover:bg-blue-100"
		>
			close
		</button>
		<div
			class="fixed left-[50%] top-[50%] z-50 max-h-[85vh] w-[90vw]
            max-w-[450px] translate-x-[-50%] translate-y-[-50%] rounded-md bg-gray-950
            p-6 shadow-lg"
			use:melt={$content}
		>
			<h2 use:melt={$title} class="m-0 text-lg font-medium text-black">First dialog</h2>
			<p use:melt={$description} class="mb-5 mt-2 leading-normal text-zinc-600">
				This is the first dialog. It contains a trigger to open a second dialog.
			</p>

			<div class="mt-6 flex justify-end gap-4">
				<button
					use:melt={$close}
					class="inline-flex h-8 items-center justify-center rounded-[4px]
                    bg-zinc-100 px-4 font-medium leading-none text-zinc-600"
				>
					Cancel
				</button>
			</div>
		</div>
		<button
			use:melt={$close}
			class="absolute right-[10px] top-[10px] inline-flex h-6 w-6
                appearance-none items-center justify-center rounded-full text-blue-800
                hover:bg-blue-100 focus:shadow-blue-400"
		>
			close
		</button>
	</div>
{/if}
