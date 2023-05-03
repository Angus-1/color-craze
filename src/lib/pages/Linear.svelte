<script>
    import Link from "$lib/components/Link.svelte";
    import Page from "$lib/components/Page.svelte";
    import Text from "$lib/components/Text.svelte";
    import { primaryBackground } from "$lib/utils/constants";
  
  
    import { colors } from "$lib/data/linear_colors";
    import Anchor from "$lib/components/Anchor.svelte";
    import CopyClipBoard from "$lib/components/Copy2Clip.svelte";
	
    
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
  
  
  
  
  <Anchor id="content" />
  <div
  class="flex flex-col items-center justify-center bg-center bg-no-repeat bg-cover page lg:bg-fixed bg-neutral-600 bg-blend-soft-light dark:bg-blend-soft-light dark:bg-neutral-700"
  id="bg"
  >
    <Text>
      <div class="text-center">
        </div>
        
      <div class = "text-2xl m-6 font-light" > Linear gradients </div>
      <label for="degrees">Degrees: {deg}</label>
  <input name="degrees" type="range" min="0" max="360" bind:value={deg}/>
  
  
  
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
                  ">
          
              </div>  
                <input name="color-1" type="color" bind:value={color1}/>	
              <br>
              <input name="color-2" type="color" bind:value={color2}/>
              </div>
  
              <div class="flip-box-back container">
                <p>{title}</p>
                linear-gradient <br>({color1.toString(16)}, <br>{color2.toString(16)});
                 
                 <br>
                
                <p>{descr}</p>
              </div>
            </div>
            <footer on:click={toggleBackFront} data-card-id={i}>{title}</footer>
          </div>
        {/each}
      </div>	
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
      /* The flip box container - set the width and height to whatever you want. We have added the border property to demonstrate that the flip itself goes out of the box on hover (remove perspective if you don't want the 3D effect */
      
      :root {
      --cardheight: 18.5rem;
        }
      .flip-box {
          background-color: transparent;
          width: 12.5rem;
          height: var(--cardheight);
          margin-left:.3rem;
          margin-right:.3rem;
          perspective: 1000px; /* Remove this if you don't want the 3D effect */
          margin-bottom:4rem;
          border-radius: 10px;
      }
      /*  container to position the front & back side */
      .flip-box-inner {
          position: relative;
          width: 100%;
          height: 100%;
          text-align: center;
          transition: transform 0.8s;
          transform-style: preserve-3d;
          border-radius: 10px;
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
          border-radius: 10px;
      }
  
      /* Style the front side */
      .flip-box-front {
          background-color: rgb(255, 251, 251);
          color:black;
          border-radius: 10px;
      }
  
      /* Style the back side */
      .flip-box-back {
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          background-color: #1F2937;
          color: #7EACC0;
          width: 12.3rem;
          height: var(--cardheight);
          margin: 0rem .4rem;
          transform: rotateY(180deg) translateX(6px);
          border-radius: 10px;
      }
  
  
      /*----------text box for colors----------------*/
  
      footer {
          width: 200px;
          font-weight: 800;
          padding: 5px 2px;
          text-align: center;
          border: 1px solid #7EACC0;
          border-top: 1px solid black;
          background-color: #1F2937;
          color: #7EACC0;
          cursor: pointer;
          transition: .3s all;
          border-radius: 10px;
      }
      
      footer:hover {
          color: #FFFFFF;
          background-color: #1E40AF;
          border: 1px solid rgb(253, 253, 253);
      }
      
      footer:active {
          color: #000;
          background-color: #888
      }
  
           
  
  
      .card {
          box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
      }
  
      
      
  
  
  
  
      
  </style>
  
  