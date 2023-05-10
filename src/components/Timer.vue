<script setup lang="ts">
import {ref} from "vue"

const INITIAL_TIME = '00:00:00'
const time = ref(INITIAL_TIME)

const HOUR_IN_SEC = 3600
const MIN_IN_SEC = 60

const timeToSec = (t: string): number => {
	const [h, m, s] = t.split(':').map(e => parseInt(e))
	if (s === undefined) return 0
	return h * HOUR_IN_SEC + m * MIN_IN_SEC + s
}

const secToTime = (s: number): string  => {
	return new Date(s * 1000).toISOString().substring(11, 19)
}

const sec = ref(0)
const timerId = ref(0)

const countDownInner = (): void => {
	sec.value--
	time.value = secToTime(sec.value)
}

const countDown = (): void => {
	timerId.value = setInterval(countDownInner, 1000)
}

const isTimerStopped = ref(true)

const startTimer = (): void => {
	sec.value = timeToSec(time.value)
	if (sec.value <= 0) return
	isTimerStopped.value = false
	countDown()
}

const StopTimer = (): void => {
	clearInterval(timerId.value)
	isTimerStopped.value = true
}
</script>

<template>
	<div class="flex items-center h-screen">
		<div class="shadow-md rounded-md mx-auto" style="width: 350px;">
			<div class="p-5 text-center">
				<h5 class="text-x1 font-semibold mb-2">Card title</h5>
				<div class="mb-4">
					<input type="time" step="1" class="outline-none" v-model="time">
				</div>
				<div class="relative mb-4">
					<div class="overflow-hidden h-2 text-xs flex rounded bg-purple-200">
						<div style="width: 30%;" class="shadow-none flex flex-col text-center whitespace-nowrap text-white justify-center bg-purple-500">
						</div>
					</div>
				</div>
				<button v-if="!isTimerStopped" class="purple-btn" type="button" @click="StopTimer()">Stop</button>
				<button v-else class="purple-btn" type="button" @click="startTimer()">Button</button>
				<button class="purple-btn" type="button">Reset</button>
			</div>
		</div>
	</div>
</template>