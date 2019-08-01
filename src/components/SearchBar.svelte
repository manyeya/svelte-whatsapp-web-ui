<script>
    let focus; 
    import { fade } from "svelte/transition";
    let focused = {}
</script>

<style lang="scss">
  .search__bar {
    display: flex;
    flex-direction: row;
    width: 100%;
    align-items: center;
    background-color: rgb(238, 238, 238);
    border-bottom: rgb(228, 228, 228) 1px solid;
    
    
  }
  .search {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    height: 40px;
    width: 100%;
    border-radius: 20px;
    margin: 1% 4%;
    background-color: white;
    transition: all 0.1s ease-in-out;
    
  }
  .search input[type="search"] {
    border: none;
    width: 70%;
    height: 90%;
    outline: none;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .search i {
    width: 20%;
    color: rgb(129, 129, 129);
    display: flex;
    align-items: center;
   
  }
</style>

<div class="search__bar">
  <div class="search" style={ focus===true ? 'box-shadow:1px 2px 5px grey;border-radius:0px;margin:0%;height:45px' : ''}>
     <i class="material-icons"  style={ focus===true ? 'cursor:pointer': ''}>{ focus===true ? 'arrow_back' : 'search'}</i>
    <input  on:focus={()=>focus = true} on:focusout={()=>focus = false} placeholder="search or start new chat" type="search" />
  </div>
</div>
