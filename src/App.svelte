<script>
  import Sidebar from "./components/Sidebar.svelte";
  import ChatBar from "./components/ChatBar.svelte";
  import SearchBar from "./components/SearchBar.svelte";
  import { onMount } from "svelte";
  import { users } from "./context/store.js";
  let chat = false;
  let profile = false;
  let users_ = [];

  onMount(async () => {
    try {
      const res = await fetch(`https://jsonplaceholder.typicode.com/users`);
      const users = await res.json();
      users_ = users
     
    } catch (error) {
      console.log(error);
    }
  });

  function openChat() {
    chat === false ? (chat = true) : (chat = false);
  }

  function closeChat() {
    chat = false;
  }

  function openProfile() {
    profile === false ? (profile = true) : (profile = false);
  }

  function closeProfile() {
    profile = false;
  }
</script>

<style>
  .main__window {
    display: flex;
    flex-direction: row;
    width: 100%;
    height: 100%;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    overflow: hidden;
  }

  .main__window aside nav,
  .main__window main nav {
    display: flex;
    flex-direction: row;
    background-color: whitesmoke;
    width: 100%;
    height: 10vh;
    z-index: 99;
    border-bottom: rgb(228, 228, 228) 1px solid;
  }

  .main__window aside .friends {
    width: 100%;
    height: 550px;
    overflow-y: auto;
    background-color: bisque;
  }

  aside {
    width: 30%;
    height: 100vh;
    background-color: whitesmoke;
    border-right: rgb(228, 228, 228) 1px solid;
    
  }
  main {
    width: 70%;
    height: 100vh;
    background-color: white;
  }
  .profile__links {
    display: flex;
    flex-direction: row;
    width: 50%;
    justify-content: center;
    align-items: center;
  }
  .friend__links {
    display: flex;
    flex-direction: row;
    width: 20%;
    justify-content: center;
    align-items: center;
  }

  .user__profile {
    width: 50%;
    height: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    cursor: pointer;
  }

  .friend__profile {
    width: 80%;
    display: flex;
    flex-direction: row;
    align-items: center;
  }
  .user__profile .img__circle {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: black;
    margin-left: 10%;
    overflow: hidden;
  }

  .friend__profile .img__circle {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: black;
    margin-left: 3%;
    overflow: hidden;
  }

  .img__circle img {
    width: 100%;
    height: 100%;
  }

  .profile__links i {
    margin-left: 15%;
    color: rgb(129, 129, 129);
    font-size: 1.4em;
    cursor: pointer;
  }

  .friend__links i {
    margin-left: 15%;
    color: rgb(129, 129, 129);
    font-size: 1.5em;
    cursor: pointer;
  }
</style>

<div class="main__window">
  <aside>
    {#if chat}
      <Sidebar on:close={closeChat} title={'New Chat'}>
        <div class="chat" />
      </Sidebar>
    {/if}
    {#if profile}
      <Sidebar on:close={closeProfile} title={'Profile'}>
        <div class="chat" />
      </Sidebar>
    {/if}
    <nav>
      <div class="user__profile">
        <div on:click={openProfile} class="img__circle">
          <img
            src="https://pbs.twimg.com/profile_images/1419305258/Conrad_Person_pic.jpg"
            alt="person" />
        </div>
      </div>
      <div class="profile__links">
        <i class="material-icons">data_usage</i>
        <i on:click={openChat} class="material-icons">chat</i>
        <i class="material-icons">more_vert</i>
      </div>
    </nav>
    <SearchBar />
    <div class="friends">
        <ChatBar username='Khutso' time='16:40' msg='What ever it is you can do it,your the choosen one.'/>
        <ChatBar username='Alice' time='12:55' msg='I love you bae' read={true}/>
        <ChatBar username='Robert' time='14:45' msg='Lets submit the quiz' read={true}/>
        <ChatBar username='Khutso' time='16:40' msg='What ever it is you can do it,your the choosen one.'/>
        <ChatBar username='Alice' time='12:55' msg='I love you bae' read={true}/>
        <ChatBar username='Robert' time='14:45' msg='Lets submit the quiz' read={true}/>
        <ChatBar username='Khutso' time='16:40' msg='What ever it is you can do it,your the choosen one.'/>
        <ChatBar username='Alice' time='12:55' msg='I love you bae' read={true}/>
        <ChatBar username='Robert' time='14:45' msg='Lets submit the quiz' read={true}/>
        <ChatBar username='cert' time='14:45' msg='Lets submit the quiz' read={true}/>
    </div>
  </aside>
  <main>
    <nav>
      <div class="friend__profile">
        <div class="img__circle">
          <img
            src="https://pbs.twimg.com/profile_images/1419305258/Conrad_Person_pic.jpg"
            alt="person" />
        </div>
      </div>
      <div class="friend__links">
        <i class="material-icons">search</i>
        <i class="material-icons">attach_file</i>
        <i class="material-icons">more_vert</i>
      </div>
    </nav>
  </main>
</div>
