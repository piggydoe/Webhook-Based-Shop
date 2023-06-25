<script>
    // @ts-ignore
    export let itemID;
    // @ts-ignore
    export let title;

    export let price;

    import { discordUser } from '../store/store'

    function sendWebhook(webHookURL, message) {
        var xhr = new XMLHttpRequest();
        xhr.open("POST", webHookURL, true);
        xhr.setRequestHeader('Content-Type', 'application/json');
        xhr.send(JSON.stringify({
            'content': message,
            'username':'AI',
        }));
    }

    const order = () => {
        sendWebhook("https://discord.com/api/webhooks/1122584457602400286/9ORmcF9lK-Q4Z1SSnoDvxhNDM7jpP_Z3DlI05hnvO-PZgbPVZy6VfKzsxpDJRcTAdHE6", `${$discordUser} ORDERED PRODUCT ID: ${itemID}`)
        alert("MESSAGE FROM S&M: Our staff will get back to you as soon as possible\nA DM will be sent.")
    }
</script>

<div class="card">
    <h1>{title}</h1>
    <p>{price}</p>
    <button class="btn" on:click={order}>ORDER - ID: {itemID}</button>
</div>

<style lang="css">
.card{
    background:#2c3e50;
    padding: 20px;
    border-radius: 10px;
    width: 70%;
}
.btn{
    border:none;
    color: #ecf0f1;
    padding:10px;
    border-radius:5px;
    width: 100%;
    cursor: pointer;
    background: #2ecc71;
}
</style>