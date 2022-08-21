<script lang="ts">
  import Anchor from "$lib/components/Anchor.svelte";

 
  let color = "text-grey-200";
  let hover = "sm:hover:text-primary-500";
 
</script>

<Anchor id="home" />
<div
  class="flex flex-col items-center justify-center bg-center bg-no-repeat bg-cover page lg:bg-fixed bg-neutral-600 bg-blend-soft-light dark:bg-blend-soft-light dark:bg-neutral-700"
  id="bg"
>
  <div class="text-center">
    <h1 class="text-5xl m-6 {color} font-light">🖌️ Color Craze 🎨  </h1>
  </div>

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
  .text-2{
  font-size: 1.8rem;  
  margin: 0rem;
  margin-top: 0rem;
  font-weight: 200;
  line-height: 3rem;
  color:rgb(215, 219, 223);
 }    
 
  .subtitle {
    font-size: 1.8rem; 
     margin: 0rem;
    font-weight: 200;
    color:rgb(215, 219, 223);
    padding-left: 3vw;
    
  }
</style>