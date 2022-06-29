<script>
    import { svg_element } from 'svelte/internal';
import { fade, fly } from 'svelte/transition';

    let frameworks = [];
	let texte = '';
	const ajouter = () => {
        if (texte=='') {
            alert("Attention vous n'avez rien ajouter");
   } 
        else {
            frameworks.push(texte);
		    frameworks = frameworks;
		    texte = '';
        }
		  
	};

	const supprimer = (index) => {
		frameworks.splice(index, 1);
		frameworks = frameworks;
	}

	const submit = (event) => {
			if (event.key === 'Enter') {
				ajouter();
			}
		}


</script>


<div class="container">
	
	<h1>Todo List</h1>
	<div class="todo-input">
		
		<input
			on:keydown={submit}
			type="text" 
			bind:value={texte}
			placeholder="A faire..."
		> 
		<button class="button-1" on:click={ajouter}>+</button>
	</div>
	 
	<ul>
		{#each frameworks as framework, index}
			<li in:fly="{{ x: -200, duration: 1000 }}" out:fly="{{ x: +200, duration: 1000 }}">
			<span>{framework}</span>
			  
			<button class="button-2" on:click={()=>supprimer(index)}><img src="src/assets/icons8-poubelle-20.svg" alt="poubelle"></button></li>
		{/each}
	</ul>
</div>

<style>
	:global(body) {
		padding: 8;
		background-color: #413636;
		color: beige;
		font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
		font-size: large;
		
	}
	
	.container	{
		margin: 0 auto;
		width: 100%;
		max-width: 28rem;
		overflow: hidden;
		margin: auto;
		text-align: center;
	}

	.todo-input	{
		display: flex;
		align-items: center;
		justify-content: space-between;
		height: 50px;
		background-color: #3f0505c9;
		border-radius: 5px;
	}

	input {
		background-color: #3f0505c9;
		outline: 0px;
		padding: 1rem;
		color: beige;
		width: 100%;
		border: none;
		border-radius: 5px;
		font-size: 1rem;
	}

	.button-1 {
  background-color: rgb(148, 60, 60);
  border-bottom-right-radius: 5px;
  border-top-right-radius: 5px;
  border-style: none;
  box-sizing: border-box;
  color: black;
  cursor: pointer;
  display: inline-block;
  font-family: "Haas Grot Text R Web", "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 30px;
  font-weight: 700;
  height: 50px;
  line-height: 20px;
  list-style: none;
  margin: 0;
  outline: none;
  padding: 10px 16px;
  position: relative;
  text-align: center;
  text-decoration: none;
  transition: color 100ms;
  vertical-align: baseline;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-1:hover,
.button-2:hover
{
  background-color: #833030;
}

ul{
	padding: 0;
}

li	{
	display: flex;
	list-style: none;
	align-items: center;
	justify-content: space-between;
	padding-bottom: 4px;
}

.button-2	{
	background-color: rgb(148, 60, 60);
	outline: none;
	border-style: none;
	border-radius: 5px;
}

.button-2 img {
	width: 30px;
	height: 30px;
}

</style>

<!-- HTML !-->



