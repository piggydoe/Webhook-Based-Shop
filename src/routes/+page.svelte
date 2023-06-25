<script lang="ts">
import Item from "../components/Item.svelte";
import { discordUser } from '../store/store'

let isModalShown = false;
let ID = "Discord Tag";
const validateID = () => {
    console.log(ID)
    discordUser.set(ID)
    isModalShown = true
}
const showIdModal = () => {
}
</script>

{#if isModalShown != true}
<div class="login">
    <input class="login-field" bind:value={ID} placeholder="enter tag or username"/>
    <button class="btn red" on:click={validateID}>Enter</button>
    <p>Disclaimer: Failing to provide a valid discord tag/username can result in (us) refusing service.</p>
</div>
{:else}
<main>
    <div class="nav">
        <div class="inner-nav">
            <h1>Welcome {$discordUser}</h1>
            <button on:click={() => location.reload(true)} class="btn red">Logout</button>
        </div>
    </div>
    <div class="shop">
        <Item itemID="1" price="$5" title="1 Month Discord Nitro"/>
        <Item itemID="2" price="COMING SOON" title="1 Year Discord Nitro"/>
    </div>
</main>

<style lang="css">

body{
    background: #34495e;
    margin:0px;
    padding:0px;
    overflow:hidden;
    color:#ecf0f1;
    height:100vh;
}

h1{
    margin:0px;
    padding:0px;
}

.shop {  display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    gap: 0px 0px;
    grid-auto-flow: row;
    grid-template-areas:
    ". . ."
    ". . ."
    ". . .";
    place-items:center;
    padding:25px;
}

.btn{
    border:none;
    color: #ecf0f1;
    padding:10px;
    border-radius:5px;
    width: 5rem;
    cursor: pointer;
}

.red{
    background: #e74c3c;
}

.nav{
    background:#2c3e50;
    height: 4rem;
    color:#ecf0f1;
    padding:10px;
}

.inner-nav{
    justify-content: space-between;
    display:flex;
    align-items:center;
    width:100%;
    height:100%;
}

</style>
{/if}