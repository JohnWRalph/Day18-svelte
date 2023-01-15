<script lang="ts">
    import { onMount } from "svelte";


    
    let name: string = "Default Name"
    
    function updateName(newName:string) {
        name = newName;
    }
    

  </script>
  
<h2>Hello {name}!</h2>

<input bind:value={name} placeholder="Enter your name" type="text">

