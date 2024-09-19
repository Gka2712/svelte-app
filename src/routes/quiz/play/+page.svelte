<script>
	const quiz=[
		["孫の手の「孫」とは誰のこと?","孫","子供","美女","母親"],
		["シルエットの語源は人物名ですが、シルエットさんのどのようなエピソードでこの言葉ができたか?","努力家","冷酷","倹約家","変人"],
		["モットーの語源はイタリア語ですが、そのもともとの意味は?","標語","声","目標","座右の銘"],
		["「@(アットマーク)は英語圏でなんと呼ばれている?」","クッキー","アルマジロ","カタツムリ","ロールケーキ"]
	];
	const answer=[3,3,2,3];
	let quiznum=0;
	let result='';
	let showresult=false;
	console.log(quiz.length);
	function handleselect(num){
		console.log(quiznum);
		if(num==answer[quiznum]){
			console.log("正解です");
			result='◯';
		}
		else{
			console.log("不正解です");
			result='×';
		}
		showresult=true;
		setTimeout(()=>{
			showresult=false;
			if(quiznum<quiz.length-1){
				quiznum++;
			}
			else{
				console.log("クイズを終了します");
			}
		},1000);
	}
</script>
<svelte:head>
	<title>Quiz</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>
<main>
	<h3>問題{quiznum+1}</h3>
	<h1>{quiz[quiznum][0]}</h1>
	<div class="quizselect">
		<button class="quizselectpos" on:click={()=>handleselect(1)}>{quiz[quiznum][1]}</button>
		<button class="quizselectpos" on:click={()=>handleselect(2)}>{quiz[quiznum][2]}</button>
		<button class="quizselectpos" on:click={()=>handleselect(3)}>{quiz[quiznum][3]}</button>
		<button class="quizselectpos" on:click={()=>handleselect(4)}>{quiz[quiznum][4]}</button>
	</div>
	{#if showresult}
		<div class="result">{result}</div>
	{/if}

</main>
<style>
.result{
	position:fixed;
	top:50%;
	left:50%;
	transform:translate(-50%,-50%);
	font-size:10em;
	font-weight:bold;
	text-align:center;
	color:red;
	
}
.quizselect{
	display:flex;
	flex-direction:column;
	margin-left:30%;
	width:40%;
}
.quizselectpos{
	margin-bottom:5%;
}

</style>