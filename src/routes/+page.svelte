

<script>
 import { Button } from "$lib/components/ui/button";
 import { Progress } from "$lib/components/ui/progress";

      let loading = false;
      let show = false;
      let progress = 0;
    
      const handleClick = () => {
        loading = true;
        progress = 0;
        barLoading();
       
        // Simulating data loading
    setTimeout(() => {
      barLoading();
      loading = false;
      show = true;
    }, 3000);
  };
    
      // Loading function
      const barLoading = () => {
    const interval = setInterval(() => {
      if (progress < 100) {
        progress += 1;
      } else {
        clearInterval(interval);
      }
    }, 20);
  };
     
    </script>
    
  <div class="wrapper">
    <div class="btn">
      {#if !loading && !show}
        <Button style="height: 50px; width: 250px;" on:click={handleClick}>
          Get a link
        </Button>
      {/if}
    
      
      {#if loading}
        <div class="progress">
          <Progress value={progress} style="height: 50px; width: 250px;" />
          <p>{`${progress}%`}</p>
        </div>
      {/if}
    
      {#if show}
        <a href="/">Here is your link</a>
      {/if}
    </div>
  </div>



  <style>

    .wrapper{
      background-color: rgb(178, 124, 124);
      width: 100%;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  </style>
    