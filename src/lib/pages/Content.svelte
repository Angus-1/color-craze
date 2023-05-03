<script>
  import Link from "$lib/components/Link.svelte";
  import Page from "$lib/components/Page.svelte";
  import Text from "$lib/components/Text.svelte";
  import { primaryBackground } from "$lib/utils/constants";


  import { colors } from "$lib/data/linear_colors";
  import Anchor from "$lib/components/Anchor.svelte";
	
  
	// @ts-ignore
	let selected;
// @ts-ignore
		$:console.log(selected)
	
	let cardBackShowing = false;
	
	// @ts-ignore
	const toggleBackFront = (e) => {
		// if same card clicked twice to toggle front and back
		// @ts-ignore
		if (selected === Number(e.target.dataset.cardId)) {
			selected = null;
			cardBackShowing = !cardBackShowing;
		} else {
			cardBackShowing = !cardBackShowing;
			selected = Number(e.target.dataset.cardId)
		}
	}

	let deg = 45

</script>




<Anchor id="content" />
<div
class="flex flex-col items-center justify-center bg-center bg-no-repeat bg-cover page lg:bg-fixed bg-neutral-600 bg-blend-soft-light dark:bg-blend-soft-light dark:bg-neutral-700"
id="bg"
>
  <Text>
	<div class="text-center">
		<h1 class="text-5xl m-6 font-light">🖌️ Colorz 🎨  </h1>
	  </div>

	  <div class=" grid grid-cols-3 gap-1 content-center">

	  <button class="bg-blue-600 hover:bg-slate-800 text-white font-bold py-2 px-4 rounded inline-flex items-center">
		<a href="/linear" class="button">Linear</a>
	  </button> 
<br>
	  <button class="bg-blue-600 hover:bg-slate-800 text-white font-bold py-2 px-4 rounded inline-flex items-center">
		<a href="/radial" class="button">Radial</a>
	  </button> 
	</div>
	<!-- add buttons redirects here in a bit -->

  </Text>

</div>



<style>
	 #bg {
    /* The image used background-image: url("/assets/images/background1.jpg"); */
    background: radial-gradient(circle 150px at 61% 0%, rgb(219, 225, 239) 0%, rgb(219, 225, 239) 50%,transparent 50%, transparent 100%),
    radial-gradient(circle 144px at 33% 100%,rgb(219, 225, 239) 0%, rgb(219, 225, 239) 50%,transparent 50%, transparent 100%),
    radial-gradient(circle 94px at 56% 36%, rgb(219, 225, 239) 0%, rgb(219, 225, 239) 50%,transparent 50%, transparent 100%),
    radial-gradient(circle 183px at 16% 59%, rgb(219, 225, 239) 0%, rgb(219, 225, 239) 50%,transparent 50%, transparent 100%),
    radial-gradient(circle 212px at 7% 86%, rgb(219, 225, 239) 0%, rgb(219, 225, 239) 50%,transparent 50%, transparent 100%),
    radial-gradient(circle 107px at 0% 19%, rgb(219, 225, 239) 0%, rgb(219, 225, 239) 50%,transparent 50%, transparent 100%),
    linear-gradient(90deg, rgb(55, 75, 129),rgb(55, 72, 129));
  }
		.color-container{
		margin: 0 0rem 1rem;
		width: 12.5rem;
		height: 12.5rem;
		background: linear-gradient(var(--deg),var(--gradient-1), var(--gradient-2));
		border-radius: 10px;
	}	
	.row {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		margin-bottom: 10%;
		
	}


	
</style>

