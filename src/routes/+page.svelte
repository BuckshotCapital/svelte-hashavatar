<script>
	import { SHA256Avatar } from '$lib/index.js';

	const defaultAdjustableHash = '2c26b46b68ffc68ff99b453c1d30413413422d706483bfa0f98a5e886266e7ae';
	let adjustable = $state(defaultAdjustableHash);
</script>

<div class="mb-8">
	<h1 class="text-xl font-bold">Hashavatars</h1>

	<p>
		SHA256Avatar is a direct port of React SHA256Avatar made by François Best. See <a
			class="font-medium text-blue-600 hover:underline dark:text-blue-500"
			href="https://francoisbest.com/posts/2021/hashvatars"
			target="_blank"
			rel="noopener">Representing SHA-256 Hashes As Avatars</a
		>
	</p>

	<p>
		SHA256Avatar examples below are also from the same linked blog post, showing that the
		implementation matches with original
	</p>
</div>

<figure class="mb-8">
	<div class="mb-2 flex justify-around">
		<SHA256Avatar
			class="h-24 w-24 sm:h-32 sm:w-32"
			hash="315f5bdb76d078c43b8ac0064e4a0164612b1fce77c869345bfc94c75894edd3"
			mapColor={function mapValueToColor({ value }) {
				const colorH = value >> 4;
				const colorS = (value >> 2) & 0x03;
				const colorL = value & 0x03;
				const normalizedH = colorH / 16;
				const normalizedS = colorS / 4;
				const normalizedL = colorL / 4;
				const h = 360 * normalizedH;
				const s = 50 + 50 * normalizedS;
				const l = 50 + 20 * normalizedL;
				return `hsl(${h}, ${s}%, ${l}%)`;
			}}
		/>
		<SHA256Avatar
			class="h-24 w-24 sm:h-32 sm:w-32"
			hash="315f5bdb76d078c43b8ac0064e4a0164612b1fce77c869345bfc94c75894edd3"
			variant="normal"
		/>
		<SHA256Avatar
			class="h-24 w-24 sm:h-32 sm:w-32"
			hash="315f5bdb76d078c43b8ac0064e4a0164612b1fce77c869345bfc94c75894edd3"
			variant="stagger"
		/>
	</div>
	<div class="flex justify-around text-center text-sm">
		<p class="w-24 sm:w-32">Without souls</p>
		<p class="w-24 sm:w-32">With souls</p>
		<p class="w-24 sm:w-32">With souls &amp; staggering</p>
	</div>
</figure>

<figure class="mb-8">
	<div class="mb-2 flex justify-around">
		<SHA256Avatar
			class="h-24 w-24 sm:h-32 sm:w-32"
			hash="2c26b46b68ffc68ff99b453c1d30413413422d706483bfa0f98a5e886266e7ae"
			variant="stagger"
		/>
		<SHA256Avatar
			class="h-24 w-24 sm:h-32 sm:w-32"
			hash="fcde2b2edba56bf408601fb721fe9b5c338d10ee429ea04fae5511b68fbf8fb9"
			variant="spider"
		/>
		<SHA256Avatar
			class="h-24 w-24 sm:h-32 sm:w-32"
			hash="34707c3f40dfa20c3902b807b627d420d6d474d9d98066ba637953d1cfd6b914"
			variant="flower"
		/>
		<SHA256Avatar
			class="h-24 w-24 sm:h-32 sm:w-32"
			hash="851cfc3d60d379af774e1e92dbd0648dd2f512ef1894ccd182ec5e05239b6f50"
			variant="gem"
		/>
	</div>
	<div class="flex justify-around text-center text-sm">
		<p class="w-24 sm:w-32">Normal</p>
		<p class="w-24 sm:w-32">Spider</p>
		<p class="w-24 sm:w-32">Flower</p>
		<p class="w-24 sm:w-32">Gem</p>
	</div>
</figure>

<figure class="mb-8">
	<div class="mb-2 flex justify-around">
		<SHA256Avatar class="h-24 w-24 sm:h-32 sm:w-32" hash={adjustable} />
	</div>
	<div class="flex justify-around text-center text-sm">
		<div>
			<label for="adjustable">Adjust the value:</label>
			<input
				id="adjustable"
				type="text"
				bind:value={adjustable}
				class="w-24 rounded-lg border-2 border-gray-600 sm:w-32"
			/>
			<button onclick={() => (adjustable = defaultAdjustableHash)}>Reset</button>
		</div>
	</div>
</figure>
