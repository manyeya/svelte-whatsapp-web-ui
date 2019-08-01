<script>
  import { fade, fly } from "svelte/transition";
  export let username;
  export let msg = "";
  export let time;
  export let read;
  export let pic;
</script>

<style>
  .friend__bar__chat {
    display: flex;
    flex-direction: row;
    width: 100%;
    height: auto;
    background-color: white;
    cursor: pointer;
  }

  .friend__bar__chat:hover {
    background-color: whitesmoke;
  }

  .friend__bar__chat .left {
    display: flex;
    flex-direction: row;
    width: 80%;
  }

  .friend__bar__chat .left .image {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 30%;
  }

  .friend__bar__chat .left .details {
    display: flex;
    flex-direction: column;
    width: 70%;
    border-bottom: rgb(228, 228, 228) 1px solid;
  }

  .friend__bar__chat .left .details .username {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    height: 50%;
  }

  .friend__bar__chat .left .details .current__msg {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    height: 50%;
  }

  .friend__bar__chat .left .details .current__msg i {
    font-size: 1.1em;
  }

  .friend__bar__chat .left .details .current__msg p {
    font-size: 1em;
  }

  .friend__bar__chat .right {
    display: flex;
    flex-direction: column;
    width: 20%;
    border-bottom: rgb(228, 228, 228) 1px solid;
  }

  .friend__bar__chat .right .time {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    width: 100%;
    height: 50%;
  }

  .friend__bar__chat .right .ticks {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    width: 100%;
    height: 50%;
  }
  .friend__bar__chat .left .image .img__circle {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background-color: black;
    overflow: hidden;
  }

  .img__circle img {
    width: 100%;
    height: 100%;
  }

  p,
  i {
    color: rgb(129, 129, 129);
  }
  b {
    color: rgb(53, 53, 53);
  }
</style>

<div class="friend__bar__chat" in:fly={{ y: 200, duration: 100 }} out:fade>
  <div class="left">
    <div class="image">
      <div class="img__circle">
        <img src={pic} alt="user" />
      </div>
    </div>
    <div class="details">
      <div class="username">
        <b>{username}</b>
      </div>
      <div class="current__msg">
        <p>
          {#if read}
            <i class="material-icons">done_all</i>
          {:else}
            <i class="material-icons">done</i>
          {/if}
          {msg.length > 25 ? msg.slice(0, 25).concat('...') : msg}
        </p>
      </div>
    </div>
  </div>
  <div class="right">
    <div class="time">
      <p>{time}</p>
    </div>
    <div class="ticks">
      <i class="material-icons">keyboard_arrow_down</i>
    </div>
  </div>
</div>
