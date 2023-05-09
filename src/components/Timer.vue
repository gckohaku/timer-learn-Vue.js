<script setup lang="ts">
</script>

<template>
	<div class="flex items-center h-screen">
		<div class="shadow-md rounded-md mx-auto" style="width: 350px;">
			<div class="p-5 text-center">
				<h5 class="text-x1 font-semibold mb-2">Card title</h5>
				<div class="mb-4">
					<input type="time" step="1" class="outline-none">
				</div>
				<div class="relative mb-4">
					<div class="overflow-hidden h-2 text-xs flex rounded bg-purple-200">
						<div style="width: 30%;"
							class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-500">
						</div>
					</div>
				</div>
				<button
					class="bg-purple-500 text-white active:bg-purple-600 font-bold uppercase text-xs px-4 py-2 rounded shadow hover:shadow-md outline-none mr-1 mb-1 ease-linear transition-all duration-150"
					type="button">
					Button
				</button>
			</div>
		</div>
	</div>
</template>