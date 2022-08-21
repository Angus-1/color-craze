<script>
  import Link from "$lib/components/Link.svelte";
  import Page from "$lib/components/Page.svelte";
  import Text from "$lib/components/Text.svelte";
  import { primaryBackground } from "$lib/utils/constants";

  export let backgroundClass = primaryBackground;
  import { colors } from "$lib/pages/colors";
	
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
	$: degString = `${deg}deg`
</script>

<Page id="content" title=" " {backgroundClass}>
  <Text>
    <div class="row">
      {#each colors as {title,color1, color2, descr,}, i}
        <div class="flip-box">
          <div class="flip-box-inner" class:show-back={selected === i}>
            <div class="flip-box-front card">
				<div class="color-container"
				style="
					--deg: {degString};
					--gradient-1:{color1};
					--gradient-2:{color2};
				"
			  ></div>
			  <label for="color-1">Color 1</label>
			<input name="color-1" type="color" bind:value={color1}/>
			<br>
			  <label for="color-2">Color 2</label>
			<input name="color-2" type="color" bind:value={color2}/>
            </div>
    
            <div class="flip-box-back container">
              <p>{title}</p>
              <p>{color1}</p>
              <p>{color2}</p>
              <p>{descr}</p>

			 
			
           

            </div>
          </div>
          <footer on:click={toggleBackFront} data-card-id={i}>{title}</footer>
        </div>
      {/each}
    </div>	
  </Text>




</Page>


<style>
		.color-container{
		margin: 0 0px 40px;
		width: 12.4rem;
		height: 10.5rem;
		background: linear-gradient(var(--deg),var(--gradient-1), var(--gradient-2))
	}	
	
  h1 {
		margin: 0 0 5px;
	}
	
	.row {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		margin-bottom: 10%;
	}
	/* The flip box container - set the width and height to whatever you want. We have added the border property to demonstrate that the flip itself goes out of the box on hover (remove perspective if you don't want the 3D effect */
	
	.flip-box {
		background-color: transparent;
		width: 200px;
		height: 310px;
		margin: 0 20px 40px;
		border: 1px solid #f1f1f1;
		perspective: 1000px; /* Remove this if you don't want the 3D effect */
	}
	/*  container to position the front & back side */
	.flip-box-inner {
		position: relative;
		width: 100%;
		height: 100%;
		text-align: center;
		transition: transform 0.8s;
		transform-style: preserve-3d;
	}

	
	
	.show-back {
		transform: rotateY(180deg);
	}

	/* Position the front and back side */
	.flip-box-front, .flip-box-back {
		position: absolute;
		width: 100%;
		height: 100%;
		-webkit-backface-visibility: hidden; /* Safari */
		backface-visibility: hidden;
	}

	/* Style the front side */
	.flip-box-front {
		background-color: rgb(255, 251, 251);
		color:black;
	}

	/* Style the back side */
	.flip-box-back {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		background-color: rgb(255, 255, 255);
		color: rgb(0, 0, 0);
		width: 12.3rem;
		height: 19.5rem;
		margin: 0rem .4rem;
		transform: rotateY(180deg) translateX(6px);
	}


	img {
		max-height: 100%;

	}	

	footer {
		width: 200px;
		font-weight: 800;
		padding: 5px 2px;
		text-align: center;
		border: 1px solid darkgray;
		border-top: 1px solid black;
/* 		box-shadow: 0 0 2px black; */
		cursor: pointer;
		transition: .3s all;
	}
	
	footer:hover {
		color: #fff;
		background-color: #000;
		border: 1px solid black;
	}
	
	footer:active {
		color: #000;
		background-color: #888
	}

		 Three columns side by side 
	.column {
		float: left;
		width: 33.3%;
		margin-bottom: 16px;
		padding: 0 8px;
	} 

	/* Display the columns below each other instead of side by side on small screens */
	 @media screen and (max-width: 650px) {
		.column {
			width: 100%;
			display: block;
		}
	}
	 
	 Add some shadows to create a card effect 
	.card {
		box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
	}

	/* Some left and right padding inside the container */
	.container {
		padding: 5px;
	}

	/* Clear floats */
	.container::after, .row::after {
		content: "";
		clear: both;
		display: table;
	} 
	
	h2 {
		margin: 5px 0 0 0;
	}	

	.title {
		color: grey;
	}

	.button {
		border: none;
		outline: 0;
		display: inline-block;
		padding: 8px;
		font-weight: bold;
		background-color: #FFF;
		text-align: center;
		cursor: pointer;
		width: 80%;
	}

	.button:hover {
		background-color: goldenrod;
	}
</style>

