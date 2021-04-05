<script lang="ts">
	import { onMount } from 'svelte';

	export let src: string, altSrc: string;
	let canvas: HTMLCanvasElement;
	let context: CanvasRenderingContext2D;
	let img: HTMLImageElement;
	let altImg: HTMLImageElement;
	let useAlt = false;
	let glitchInterval: ReturnType<typeof setInterval>;
	let altImageInterval: ReturnType<typeof setInterval>;

	onMount(() => {
		context = canvas.getContext('2d');
		img = new Image();
		altImg = new Image();
		img.onload = () => {
			initCanvas();
		};
		img.src = src;
		altImg.src = altSrc;
	});

	const randomBetween = (a: number, b: number) => {
		return ~~(Math.random() * (b - a) + a);
	};

	const glitch = (width: number, height: number) => {
		for (let i = 0; i < randomBetween(1, 15); i++) {
			let x = Math.random() * (width - width * 0.7);
			let y = Math.random() * height;
			let hSlices = width - x;
			let vSlices = randomBetween(5, height / 4);
			if (randomBetween(1, 20) > 17) {
				context.drawImage(altImg, 0, 0, width, height);
			}
			context.drawImage(canvas, 0, y, hSlices, vSlices, x, y, hSlices, vSlices);
			context.drawImage(canvas, hSlices, y, x, vSlices, 0, y, x, vSlices);
		}
	};

	const reset = (width: number, height: number) => {
		context.rect(0, 0, width, height);
		context.fill();
	};

	const initCanvas = () => {
		canvas.width = img.width;
		canvas.height = img.height;
		const { width, height } = canvas;

		glitchInterval = setInterval(() => {
			reset(width, height);
			context.drawImage(img, 0, 0, width, height);
			setTimeout(() => {
				glitch(width, height);
			}, randomBetween(4000, 6000));
		}, 300);

		altImageInterval = setInterval(() => {
			useAlt = true;
			setTimeout(() => {
				useAlt = false;
			}, randomBetween(800, 1500));
		}, randomBetween(8500, 10000));
	};
</script>

<canvas bind:this={canvas} />
