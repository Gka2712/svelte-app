<script>
    import {goto} from '$app/navigation'
    function handleStart(){
        goto('/quiz/play',{replace:true})
    }
</script>
<svelte:head>
	<title>Quiz</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>
<main>
    <h1>Quiz</h1>
    <button on:click={handleStart}>開始する</button>
</main>
<style>
</style>