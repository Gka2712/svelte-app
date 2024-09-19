<script>
    let chat="";
    let chattext=[];
    let chatplayer=[];
    let screenplayer='A';
    function handleSend(){
        if(chat.trim()!=""){
            chattext=[...chattext,chat];
            chat="";
            chatplayer.push(screenplayer);
        }
    }
    function handleSwitch(){
        console.log(chattext);
        if(screenplayer=='A'){
            screenplayer='B';
        }
        else{
            screenplayer='A';
        }
        
    }
</script>
<svelte:head>
	<title>chat</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>
<main>
    <h1>Chat App</h1>
    <p>このチャットは今、プレイヤー{screenplayer}になっています</p>
    <input type="text" bind:value={chat} class="chat"/>
    <button on:click={handleSend}>送信する</button>
    <button on:click={handleSwitch}>切替える</button>
    <div class="container">
        {#each chattext as chat,index}
            <div class="messageshape {chatplayer[index]===screenplayer? 'chatright': 'chatleft'}">
                <div class="containmessage">
                    {chat}
                </div>
            </div>
            
        {/each}
    </div>
</main>
<style>
    .container{
        margin-top:5%;
        margin-left:25%;
        border:solid 1px black;
        width:60%;
        min-height:200px;
        background-color:lightblue;
        display:flex;
        flex-direction:column;
    }
    .chatleft{
        align-self:flex-start;
        background-color:white;
    }
    .chatright{
        align-self:flex-end;
        background-color:lightgreen;
    }
    .containmessage{
        word-wrap:break-word;
    }
    .messageshape{
        display:inline-block;
        color:black;
        border-radius:30%;
        text-align:left;
        padding-top:1%;
        padding-left:5%;
        padding-right:5%;
        margin-top:1%;
        max-width:50%;
        word-wrap:break-word;
    }
    .chat{
        margin-left:30%;
    }
</style>